set(APNG_SOURCES
  apngimagehandler_p.h
  apngimagehandler.cpp
  apngimageplugin.cpp
  apngimageplugin.h
  apngreader_p.h
  apngreader.cpp
)

qt_add_plugin(ApngImagePlugin SHARED)

target_sources(ApngImagePlugin PRIVATE ${APNG_SOURCES})

target_link_libraries(ApngImagePlugin PRIVATE 
  Qt${APNG_QT_VERSION}::Core
  Qt${APNG_QT_VERSION}::Gui
  png_static
  zlibstatic
)

get_target_property(_png_include png_static INCLUDE_DIRECTORIES)
target_include_directories(ApngImagePlugin PRIVATE ${_png_include})

target_compile_definitions(ApngImagePlugin PRIVATE
  QT_DEPRECATED_WARNINGS
  QT_ASCII_CAST_WARNINGS
)

set_target_properties(ApngImagePlugin PROPERTIES
  AUTOMOC ON
  LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/plugins/imageformats"
  LIBRARY_OUTPUT_NAME qapng
)
