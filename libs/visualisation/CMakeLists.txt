find_package(GLUT REQUIRED)
find_package(Threads REQUIRED)
set(OpenGL_GL_PREFERENCE LEGACY)
find_package(OpenGL REQUIRED)
find_package(Eigen3 REQUIRED)
message("Eigen3 path: ${EIGEN3_INCLUDE_DIR}")
message("GLUT path: ${GLUT_INCLUDE_DIR}")
set(eqviolib_visualisation_SOURCE_FILES
    src/Plotter.cpp
)

set(eqviolib_visualisation_HEADER_FILES
    include/Plotter.h
    include/PlotDataTypes.h
)

add_library(eqviolib_visualisation
    ${eqviolib_visualisation_HEADER_FILES}
    ${eqviolib_visualisation_SOURCE_FILES}
)

target_include_directories(eqviolib_visualisation
    PRIVATE include
    PRIVATE ${EIGEN3_INCLUDE_DIR}
    PRIVATE ${GLUT_INCLUDE_DIRS}
    PRIVATE ${OPENGL_INCLUDE_DIR}
)

target_link_libraries(eqviolib_visualisation
	${GLUT_LIBRARIES}
    ${OPENGL_LIBRARIES}
    ${CMAKE_THREAD_LIBS_INIT}
)
