cmake_minimum_required(VERSION 3.20)

project(rosidl_generator_cpp)

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)

ament_index_register_resource("rosidl_generator_packages")

ament_python_install_package(${PROJECT_NAME})

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

# Where the extras find this package's executable, Python module and
# templates: relative to the installed CMake config, or absolute when the
# config files are installed apart (AMENT_CMAKE_CONFIG_INSTALL_PREFIX).
ament_package_install_prefix(_install_prefix)
ament_package(
  CONFIG_EXTRAS "rosidl_generator_cpp-extras.cmake.in"
)

install(
  PROGRAMS bin/rosidl_generator_cpp
  DESTINATION lib/rosidl_generator_cpp
)
install(
  DIRECTORY cmake resource
  DESTINATION share/${PROJECT_NAME}
)
