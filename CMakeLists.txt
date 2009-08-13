project(iTaSC)
cmake_minimum_required(VERSION 2.6)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE RelWithDebInfo)
endif(NOT CMAKE_BUILD_TYPE)

set( ITASC_VERSION 0.0.1 )
string( REGEX MATCHALL "[0-9]+" ITASC_VERSIONS ${ITASC_VERSION} )
list( GET ITASC_VERSIONS 0 ITASC_VERSION_MAJOR)
list( GET ITASC_VERSIONS 1 ITASC_VERSION_MINOR)
list( GET ITASC_VERSIONS 2 ITASC_VERSION_PATCH)
message( "iTaSC Library version ${VERSION} (${ITASC_VERSION_MAJOR}.${ITASC_VERSION_MINOR}.${ITASC_VERSION_PATCH})" )


set( CMAKE_INSTALL_PREFIX ./install/ CACHE PATH "Installation directory" )
message( "Setting installation directory to ${CMAKE_INSTALL_PREFIX}" )

set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake_modules/)
## Find KDL
set(KDL_INSTALL /usr/local)
find_package(KDL REQUIRED PATHS /usr/local)
## Find Eigen2
find_package(Eigen2 REQUIRED)


ADD_SUBDIRECTORY(src)
