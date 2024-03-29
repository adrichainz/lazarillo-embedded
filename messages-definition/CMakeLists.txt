cmake_minimum_required(VERSION 3.16)

project(messages-definition VERSION 1.0.0 LANGUAGES CXX)

set(_include_dir inc)

set(PROJECT_SOURCES
    ${_include_dir}/messages-definition/factory/message_factory.h
    ${_include_dir}/messages-definition/event_connection_status.h
    ${_include_dir}/messages-definition/event_reboot.h
    ${_include_dir}/messages-definition/i_base_message.h
    ${_include_dir}/messages-definition/message_header.h
    ${_include_dir}/models/connection_status.h
    ${_include_dir}/topics/topics.h
    src/factory/message_factory.cpp
    src/i_base_message.cpp
)

add_library(${PROJECT_NAME} SHARED ${PROJECT_SOURCES})

lzr_link_qt(${PROJECT_NAME})

set_target_properties(${PROJECT_NAME} PROPERTIES
    VERSION ${PROJECT_VERSION}
    SOVERSION 1
)

target_include_directories(${PROJECT_NAME} PUBLIC inc)

target_link_libraries(${PROJECT_NAME} PUBLIC serialization)
