cmake_minimum_required(VERSION 3.8)

project(rabbitmq-c_vendor)

# find dependencies

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_vendor_package REQUIRED)

set(RABBITMQC_CXX_FLAGS "${CMAKE_CXX_FLAGS}")

ament_vendor(rabbitmq-c_vendor
  SATISFIED ${rabbitmq-c_FOUND}
  VCS_URL https://github.com/alanxz/rabbitmq-c.git
  VCS_VERSION v0.15.0
  GLOBAL_HOOK
  CMAKE_ARGS
    "-DCMAKE_CXX_FLAGS=${RABBITMQC_CXX_FLAGS}"
    -DBUILD_EXAMPLES:BOOL=OFF
    -DBUILD_TESTING:BOOL=OFF
    -DBUILD_TOOLS:BOOL=OFF
    -DBUILD_TOOLS_DOCS:BOOL=OFF
)
ament_package(
  CONFIG_EXTRAS "rabbitmq-c_vendor-extras.cmake.in"
)
