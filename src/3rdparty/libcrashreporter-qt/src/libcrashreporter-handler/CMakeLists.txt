# message(FATAL_ERROR "${CMAKE_CURRENT_LIST_DIR}/../../3rdparty/breakpad")

list(APPEND crashreporter-handler_INCLUDE_DIRECTORIES
    ${CMAKE_CURRENT_LIST_DIR}/../../3rdparty/breakpad
    ${QT_QTCORE_INCLUDE_DIR}
)

list(APPEND crashreporter-handler_SOURCES
    Handler.cpp
)

list(APPEND crashreporter-handler_LIBRARIES
    crashreporter-breakpad
)

include_directories(${crashreporter-handler_INCLUDE_DIRECTORIES})
add_library(crashreporter-handler STATIC ${crashreporter-handler_SOURCES})
target_link_libraries(crashreporter-handler ${crashreporter-handler_LIBRARIES})
qt5_use_modules(crashreporter-handler Core)

if(WIN32)
    add_definitions( -DUNICODE ) #-fshort-wchar )
endif()
