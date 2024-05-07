set(PNG_SHARED OFF)
set(SKIP_INSTALL_ALL ON)
get_target_property(ZLIB_INCLUDE_DIRS zlibstatic INCLUDE_DIRECTORIES)
add_subdirectory(src EXCLUDE_FROM_ALL)

set_target_properties(png_static PROPERTIES POSITION_INDEPENDENT_CODE On)
