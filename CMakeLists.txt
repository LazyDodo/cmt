cmake_minimum_required(VERSION 3.00)
project(cmtest)

ENABLE_TESTING()

SET(CPACK_PACKAGE_NAME "cmtest")
SET(CPACK_PACKAGE_VENDOR "cmtestvendor")
SET(CPACK_SOURCE_PACKAGE_FILE_NAME "cmake-2.5.0")

add_executable(cmt test.cpp)

install(TARGETS cmt
        CONFIGURATIONS Debug
        RUNTIME DESTINATION Debug/bin)

install(TARGETS cmt
        CONFIGURATIONS Release
        RUNTIME DESTINATION Release/bin)

include(CPack)

add_test(NAME cmt_test_pass COMMAND $<TARGET_FILE:cmt>)
add_test(NAME cmt_test_fail COMMAND $<TARGET_FILE:cmt> fail)