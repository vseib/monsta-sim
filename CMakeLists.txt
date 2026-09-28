cmake_minimum_required(VERSION 3.16)
project(monsta_sim VERSION 0.01 LANGUAGES C CXX)

###############
## Configure ##
###############

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

# set build type
set(CMAKE_BUILD_TYPE Release)
set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# set output directories
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# find Qt 
find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Widgets)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Widgets)

###########
## Build ##
###########

add_executable(monsta_sim 
    main.cpp
    Monsta/MonstaMain.cpp
    Monsta/MonstaDefs.cpp
    Monsta/games/game.c
    Monsta/games/game.h
    Monsta/games/ping.c
    Monsta/games/feedme.c
    Monsta/games/spaceFlight.c
    Monsta/games/amazingMaze.c
    Monsta/games/glider.c
    Monsta/games/example.c     # include your game here
    GUI/MonstaWidget.cpp
    GUI/MainWindow.cpp
    GUI/licensepage.h
    GUI/licensepage.cpp
    GUI/versionpage.h
    GUI/versionpage.cpp
    GUI/keyboardwindow.cpp
    GUI/keyboardwindow.h
)

target_link_libraries(monsta_sim PRIVATE
    Qt${QT_VERSION_MAJOR}::Widgets
)

# show the compiler that we are in the matrix
target_compile_definitions(monsta_sim PRIVATE
    SIMULATOR
)


