configure_file(loggerui.json.in "${CMAKE_CURRENT_BINARY_DIR}/loggerui.json")

set(SRC
    logdialog.h
    logdialog.cpp
    loggeruiplugin.h
    loggeruiplugin.cpp
    showlogdialogaction.h
    showlogdialogaction.cpp
)

add_library(loggerui MODULE ${SRC})

set_target_properties(loggerui PROPERTIES
    CXX_STANDARD             11
    VERSION                  ${VERSION}
    SOVERSION                ${VERSION_MAJOR}
    RUNTIME_OUTPUT_DIRECTORY "${PLUGIN_OUTPUT_DIRECTORY}"
    LIBRARY_OUTPUT_DIRECTORY "${PLUGIN_OUTPUT_DIRECTORY}"
)

target_include_directories(loggerui PUBLIC "${CMAKE_CURRENT_BINARY_DIR}")
target_link_libraries(loggerui Qt5::Widgets nitroshare)

install(TARGETS loggerui
    DESTINATION "${INSTALL_PLUGIN_PATH}"
)
