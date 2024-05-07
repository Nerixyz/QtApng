set(apng_sample_sources
    main.cpp
    widget.cpp
    widget.ui
    apng_sample.qrc
)

if(COMMAND qt_add_executable)
  qt_add_executable(ApngSample WIN32 ${apng_sample_sources})
else()
  add_executable(ApngSample WIN32 ${apng_sample_sources})
endif()

target_link_libraries(ApngSample PRIVATE
  Qt${APNG_QT_VERSION}::Core
  Qt${APNG_QT_VERSION}::Gui
  Qt${APNG_QT_VERSION}::Widgets
)

set_target_properties(
  ApngSample
  PROPERTIES AUTOMOC ON
             AUTORCC ON
             AUTOUIC ON
             RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}"
)
# To actually run the example, you need to run [win/mac/linux]deployqt