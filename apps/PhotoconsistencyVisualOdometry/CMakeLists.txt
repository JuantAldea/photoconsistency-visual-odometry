# Include the phovo include files
include_directories( ${PHOVO_SOURCE_DIR}/phovo/include )
include_directories( ${PHOVO_SOURCE_DIR}/third_party )

# Declare the target (an executable)
add_executable( PhotoconsistencyVisualOdometry PhotoconsistencyVisualOdometry.cpp )

if( ${PHOVO_WITH_CERES} MATCHES "ON" )
  target_link_libraries( PhotoconsistencyVisualOdometry ${OpenCV_LIBS} ${CERES_LIBRARIES} ${Boost_LIBRARIES} )
else()
  target_link_libraries( PhotoconsistencyVisualOdometry ${OpenCV_LIBS} ${Boost_LIBRARIES} )
endif()

# Set optimized building:
if( CMAKE_COMPILER_IS_GNUCXX AND NOT CMAKE_BUILD_TYPE MATCHES "Debug" )
  SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O3 -mtune=native")
endif()
