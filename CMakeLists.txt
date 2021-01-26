cmake_minimum_required(VERSION 3.16)
project(DSP101-Book-JUCE)

set(CMAKE_EXPORT_COMPILE_COMMANDS TRUE)

#adding my own custom git functions, to save some boilerplate:
include (CMake/GitFunctions.cmake)

#calling my custom function to grab JUCE 6 from git:
#update_from_git(juce "https://github.com/juce-framework/juce" master)

#Adds all the module sources so they appear correctly in the IDE
set_property(GLOBAL PROPERTY USE_FOLDERS YES)
option(JUCE_ENABLE_MODULE_SOURCE_GROUPS "Enable Module Source Groups" ON)

#set any of these to "ON" if you want to build one of the juce examples
#or extras (Projucer/AudioPluginHost, etc):
option(JUCE_BUILD_EXTRAS "Build JUCE Extras" OFF)
option(JUCE_BUILD_EXAMPLES "Build JUCE Examples" OFF)

#adding juce as a subdirectory:
add_subdirectory(External/JUCE)

option(BUILD_EXAMPES "Build examples" ON)

if (${BUILD_EXAMPES})
    #adding any custom modules you might have:
    #add_subdirectory(Modules)

    #adding project folders:
    add_subdirectory(Examples)
endif()
