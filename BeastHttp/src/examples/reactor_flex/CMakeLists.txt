cmake_minimum_required(VERSION 3.11)

set(BEASTHTTP_EXAMPLE_NAME reactor_flex)

file(GLOB HEADS ${BEASTHTTP_EXAMPLES_DIR}/${BEASTHTTP_EXAMPLE_NAME}/*.hxx)
file(GLOB SRCS ${BEASTHTTP_EXAMPLES_DIR}/${BEASTHTTP_EXAMPLE_NAME}/*.cxx)

add_executable(${BEASTHTTP_EXAMPLE_NAME} ${BEASTHTTP_HEADS} ${HEADS} ${SRCS})

target_link_libraries(${BEASTHTTP_EXAMPLE_NAME} Boost::system Boost::thread pthread)

if(BEASTHTTP_BUILD_STATIC_LIBS)
    target_link_libraries(${BEASTHTTP_EXAMPLE_NAME} asio beast asio-ssl)
endif()

target_link_libraries(${BEASTHTTP_EXAMPLE_NAME} OpenSSL::SSL OpenSSL::Crypto)
