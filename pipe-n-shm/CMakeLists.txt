project(pns CXX C)
cmake_minimum_required(VERSION 2.8.2)

include_directories(
    "${pns_SOURCE_DIR}/src"
)

add_executable(main
    "${pns_SOURCE_DIR}/src/mainParent.cpp"
    "${pns_SOURCE_DIR}/src/childA.cpp"
    "${pns_SOURCE_DIR}/src/childB.cpp"
)

