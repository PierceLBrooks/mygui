set(PROJECTNAME MyGUI.DirectXPlatform)

include_directories(
	include
	${MYGUI_SOURCE_DIR}/MyGUIEngine/include
	${DirectX_INCLUDE_DIR}
	${MYGUI_SOURCE_DIR}/Common
)

include(${PROJECTNAME}.list)

add_library(${PROJECTNAME} STATIC ${HEADER_FILES} ${SOURCE_FILES})

add_dependencies(${PROJECTNAME} MyGUIEngine)

target_link_libraries(${PROJECTNAME} ${DirectX_LIBRARIES} MyGUIEngine)
link_directories(${DirectX_LIBRARY_DIRS})

# installation rules
install(FILES ${HEADER_FILES}
	DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}/MYGUI"
)
mygui_install_target(${PROJECTNAME} "")
