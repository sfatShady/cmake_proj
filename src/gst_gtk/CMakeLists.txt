SET (TARGET_NAME "gst_gtk")
AUX_SOURCE_DIRECTORY (. SRC_FILES)
SET (EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/output)
SET (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O3")
SET(ENV{PKG_CONFIG_PATH} /usr/lib64/pkgconfig)
find_package(PkgConfig)
pkg_search_module(GTK gtk+-2.0)
pkg_search_module(GST gstreamer-1.0)
pkg_search_module(GLIB glib-2.0)
INCLUDE_DIRECTORIES (${GTK_INCLUDE_DIRS} ${GST_INCLUDE_DIRS} ${GLIB_INCLUDE_DIRS})
ADD_EXECUTABLE(${TARGET_NAME} ${SRC_FILES})
TARGET_LINK_LIBRARIES(${TARGET_NAME} ${GTK_LIBRARIES} ${GLIB_LIBRARIES} ${GST_LIBRARIES})
INSTALL(TARGETS ${TARGET_NAME} RUNTIME DESTINATION bin) 
