# Copyright (C) 2018 LuaDist
# Submitted by Matthias Petermann.
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project ( luamqttc C )
cmake_minimum_required ( VERSION 2.8 )
include ( cmake/dist.cmake )

include_directories ( src deps/lua-compat-5.2 deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src C:/my_lua/include)

set ( INCLUDE_COMPAT
    deps/lua-compat-5.2/compat-5.2.h
)

set ( SRC_COMPAT
	deps/lua-compat-5.2/compat-5.2.c
)

set ( INCLUDE_MQTT
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTConnect.h
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTFormat.h
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTPacket.h
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTPublish.h
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTSubscribe.h
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTUnsubscribe.h
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/StackTrace.h
)

set ( SRC_MQTT
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTConnectClient.c
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTConnectServer.c
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTDeserializePublish.c
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTFormat.c
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTPacket.c
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTSerializePublish.c
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTSubscribeClient.c
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTSubscribeServer.c
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTUnsubscribeClient.c
	deps/org.eclipse.paho.mqtt.embedded-c/MQTTPacket/src/MQTTUnsubscribeServer.c
)

set ( INCLUDE
	src/luamqttpacket.h
)

set ( SRC
    src/luamqttpacket.c
)

add_library(mqttpacket SHARED ${SRC} ${SRC_COMPAT} ${SRC_MQTT})
target_link_libraries(mqttpacket C:/my_lua/bin/liblua.dll)

install_library(mqttpacket)

#INCLUDE_DIRECTORIES(/Users/yongke/.luaver/lua/5.1.5/include/)
#TARGET_LINK_LIBRARIES(luamqttpacket lua.5.1)

#INCLUDE_DIRECTORIES(/usr/local/include/lua5.2/)
#TARGET_LINK_LIBRARIES(luamqttpacket lua.5.2)

#INCLUDE_DIRECTORIES(/usr/local/include/lua5.3/)
#TARGET_LINK_LIBRARIES(luamqttpacket lua.5.3)
