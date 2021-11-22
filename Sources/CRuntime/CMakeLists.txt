add_library(CRuntime SHARED 
  dummy.c)

target_include_directories(CRuntime PUBLIC
  include)
  
set_target_properties(CRuntime PROPERTIES
    INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_SOURCE_DIR}/include)
	
	
	swift_install(TARGETS CRuntime
	  EXPORT CRuntime)