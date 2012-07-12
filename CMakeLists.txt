cmake_minimum_required (VERSION 2.8) 
project(user-migration)

find_package (PkgConfig)
pkg_check_modules (CACHED_SESSIONMIGRATION_DEPS REQUIRED "glib-2.0;gio-2.0")

add_subdirectory(src)

file(COPY tests
     DESTINATION ${PROJECT_BINARY_DIR})
add_custom_target(check
                  COMMAND nosetests3
                  DEPENDS session-migration)

