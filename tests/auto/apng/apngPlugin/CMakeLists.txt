set(apng_test_sources tst_apngplugin.cpp tst_apngplugin.qrc)

if(COMMAND qt_add_executable)
  qt_add_executable(ApngTests ${apng_test_sources})
else()
  add_executable(ApngTests ${apng_test_sources})
endif()

target_link_libraries(ApngTests PRIVATE
  Qt${APNG_QT_VERSION}::Test
  Qt${APNG_QT_VERSION}::Core
  Qt${APNG_QT_VERSION}::Gui
)

set_target_properties(
  ApngTests
  PROPERTIES AUTOMOC ON
             AUTORCC ON
             RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}"
)
# To actually run the tests, you need to run [win/mac/linux]deployqt
