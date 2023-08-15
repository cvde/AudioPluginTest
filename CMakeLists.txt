cmake_minimum_required(VERSION 3.15)

project(AUDIO_PLUGIN_EXAMPLE VERSION 0.0.1)

add_subdirectory(JUCE)

juce_add_plugin(AudioPluginExample
    PLUGIN_MANUFACTURER_CODE Juce
    PLUGIN_CODE Dem0
    FORMATS LV2
    PRODUCT_NAME "Audio Plugin Example")

target_sources(AudioPluginExample
    PRIVATE
        PluginEditor.cpp
        PluginProcessor.cpp)

target_compile_definitions(AudioPluginExample
    PUBLIC
        JUCE_WEB_BROWSER=0
        JUCE_USE_CURL=0
        JUCE_VST3_CAN_REPLACE_VST2=0)

target_link_libraries(AudioPluginExample
    PRIVATE
        juce::juce_audio_utils
    PUBLIC
        juce::juce_recommended_config_flags
        juce::juce_recommended_lto_flags
        juce::juce_recommended_warning_flags)
