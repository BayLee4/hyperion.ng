# Define the current source locations
SET(CURRENT_HEADER_DIR ${CMAKE_SOURCE_DIR}/include/grabber)
SET(CURRENT_SOURCE_DIR ${CMAKE_SOURCE_DIR}/libsrc/grabber/drm)

# Find X11
find_package(X11 REQUIRED)

include_directories( ${X11_INCLUDES} )

FILE ( GLOB DRMGrabberSOURCES "${CURRENT_HEADER_DIR}/DRM*.h"  "${CURRENT_SOURCE_DIR}/*.h"  "${CURRENT_SOURCE_DIR}/*.cpp" )
add_library( drm-grabber ${DRMGrabberSOURCES} )

target_link_libraries(drm-grabber
	hyperion
	${CMAKE_DL_LIBS}
	${X11_LIBRARIES}
	${X11_Xrandr_LIB}
	${X11_Xrender_LIB}
	${QT_LIBRARIES}
)
