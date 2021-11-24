add_library(CRuntime SHARED 
  dummy.c)

target_include_directories(CRuntime PUBLIC
  include)
  
set_target_properties(CRuntime PROPERTIES
    INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_SOURCE_DIR}/include)

get_swift_host_os(swift_os)
set(swift_dir swift)

install(TARGETS CRuntime
    EXPORT CRuntime
    ARCHIVE DESTINATION lib/${swift_dir}/${swift_os}
    LIBRARY DESTINATION lib/${swift_dir}/${swift_os}
    RUNTIME DESTINATION bin)

    install(FILES
      include/module.modulemap
      DESTINATION lib/${swift_dir}/CRuntime
      RENAME module.map)
	  
      install(FILES
        include/CRuntime.h
	DESTINATION lib/${swift_dir}/CRuntime)