# Audio Stream Playback Plugin
#
# Plays standard streaming audio formats (MP3, FLAC, WAV, OGG Vorbis)
# using lightweight single-header libraries (dr_libs, stb_vorbis).

cmake_minimum_required(VERSION 3.16)
project(playback_audio_stream C)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")
include(PlaybackPlugin)

add_library(audio_stream_playback SHARED
    audio_stream_plugin.c
    decoder_wav.c
    decoder_mp3.c
    decoder_flac.c
    decoder_vorbis.c
    metadata.c
)
target_include_directories(audio_stream_playback PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})
rv_set_plugin_properties(audio_stream_playback)
