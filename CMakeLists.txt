cmake_minimum_required(VERSION 3.22)
project(Tulatone VERSION 0.1.0)

set(CMAKE_CXX_STANDARD 17)

# Pon la carpeta de JUCE junto a este archivo: Tulatone/JUCE
add_subdirectory(JUCE)

juce_add_plugin(Tulatone
    COMPANY_NAME "Tula"
    IS_SYNTH FALSE
    NEEDS_MIDI_INPUT FALSE
    NEEDS_MIDI_OUTPUT FALSE
    PLUGIN_MANUFACTURER_CODE Tula
    PLUGIN_CODE Tltn
    FORMATS VST3
    PRODUCT_NAME "Tulatone")

target_sources(Tulatone PRIVATE
    Source/PluginProcessor.cpp
    Source/PluginEditor.cpp)

target_compile_definitions(Tulatone PUBLIC
    JUCE_WEB_BROWSER=0
    JUCE_USE_CURL=0
    JUCE_VST3_CAN_REPLACE_VST2=0)

target_link_libraries(Tulatone PRIVATE
    juce::juce_audio_utils
    PUBLIC
    juce::juce_recommended_config_flags
    juce::juce_recommended_warning_flags)
