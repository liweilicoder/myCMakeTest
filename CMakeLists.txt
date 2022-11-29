cmake_minimum_required(VERSION 3.15)
project(Tutorial VERSION 1.0)
SET(SRC_LIST tutorial.cpp)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

configure_file(TutorialConfig.h.in TutorialConfig.h)

option(USE_MYMATH "Use tutorial provide math implementation" OFF)

if (USE_MYMATH)
    add_subdirectory(MathFunctions)
    list(APPEND EXTRA_LIBS MathFunctions)
    # list(APPEND EXTRA_INCLUDES ${PROJECT_SOURCE_DIR}/MathFunctions)
endif()

add_executable(${PROJECT_NAME} ${SRC_LIST})

target_link_libraries(${PROJECT_NAME} PUBLIC ${EXTRA_LIBS})
target_include_directories(${PROJECT_NAME} PUBLIC 
                            ${PROJECT_BINARY_DIR} 
                            # ${EXTRA_INCLUDES}
                            )