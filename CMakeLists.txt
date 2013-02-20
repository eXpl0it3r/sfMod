cmake_minimum_required (VERSION 2.6)
project (sfMod)

set(INCROOT  ${PROJECT_SOURCE_DIR}/include)
set(SRCROOT  ${PROJECT_SOURCE_DIR}/src)
set(SRCSFMOD ${SRCROOT}/sfMod)

set(SRCLIBMODPLUG ${PROJECT_SOURCE_DIR}/libmodplug)

include_directories(${INCROOT})
include_directories(${SRCLIBMODPLUG})
include_directories(${SRCLIBMODPLUG}/libmodplug)

set(CMAKE_DEBUG_POSTFIX "_d")

set(LIBRARY_OUTPUT_PATH "${PROJECT_BINARY_DIR}/lib")

add_library(sfMod STATIC
              ${INCROOT}/sfMod.h
              ${SRCSFMOD}/sfMod.cpp
              ${SRCLIBMODPLUG}/modplug.h
              ${SRCLIBMODPLUG}/load_pat.h
              ${SRCLIBMODPLUG}/tables.h
              ${SRCLIBMODPLUG}/libmodplug/it_defs.h
              ${SRCLIBMODPLUG}/libmodplug/sndfile.h
              ${SRCLIBMODPLUG}/libmodplug/stdafx.h
              ${SRCLIBMODPLUG}/sndmix.cpp
              ${SRCLIBMODPLUG}/fastmix.cpp
              ${SRCLIBMODPLUG}/load_669.cpp
              ${SRCLIBMODPLUG}/load_abc.cpp
              ${SRCLIBMODPLUG}/load_amf.cpp
              ${SRCLIBMODPLUG}/load_ams.cpp
              ${SRCLIBMODPLUG}/load_dbm.cpp
              ${SRCLIBMODPLUG}/load_dmf.cpp
              ${SRCLIBMODPLUG}/load_dsm.cpp
              ${SRCLIBMODPLUG}/load_far.cpp
              ${SRCLIBMODPLUG}/load_it.cpp
              ${SRCLIBMODPLUG}/load_j2b.cpp
              ${SRCLIBMODPLUG}/load_mdl.cpp
              ${SRCLIBMODPLUG}/load_med.cpp
              ${SRCLIBMODPLUG}/load_mid.cpp
              ${SRCLIBMODPLUG}/load_mod.cpp
              ${SRCLIBMODPLUG}/load_mt2.cpp
              ${SRCLIBMODPLUG}/load_mtm.cpp
              ${SRCLIBMODPLUG}/load_okt.cpp
              ${SRCLIBMODPLUG}/load_pat.cpp
              ${SRCLIBMODPLUG}/load_psm.cpp
              ${SRCLIBMODPLUG}/load_ptm.cpp
              ${SRCLIBMODPLUG}/load_s3m.cpp
              ${SRCLIBMODPLUG}/load_stm.cpp
              ${SRCLIBMODPLUG}/load_ult.cpp
              ${SRCLIBMODPLUG}/load_umx.cpp
              ${SRCLIBMODPLUG}/load_wav.cpp
              ${SRCLIBMODPLUG}/load_xm.cpp
              ${SRCLIBMODPLUG}/mmcmp.cpp
              ${SRCLIBMODPLUG}/modplug.cpp
              ${SRCLIBMODPLUG}/snd_dsp.cpp
              ${SRCLIBMODPLUG}/snd_flt.cpp
              ${SRCLIBMODPLUG}/snd_fx.cpp
              ${SRCLIBMODPLUG}/sndfile.cpp
            )
            
add_definitions(-D_CRT_SECURE_NO_WARNINGS -D_CRT_NONSTDC_NO_DEPRECATE)
            
install (TARGETS sfMod DESTINATION lib)
install (FILES ${INCROOT}/sfMod.h DESTINATION include)
