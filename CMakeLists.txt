cmake_minimum_required( VERSION 2.8 ) 
project( h264-analysis-tool )

set( NAME_SRC
    src/main.cpp
    src/vis.cpp
	src/macroblockinfo.cpp
	src/zlib_buffer.cpp
)
set( NAME_HEADERS       
	include/macroblockinfo.h
	include/zlib_buffer.h
)
set( JM_NAME_HEADERS      
	ldecod/inc/header.h
	ldecod/inc/annexb.h
	ldecod/inc/biaridecod.h
	ldecod/inc/block.h
	ldecod/inc/cabac.h
	ldecod/inc/configfile.h
	ldecod/inc/context_ini.h
	ldecod/inc/contributors.h
	ldecod/inc/dec_statistics.h
	ldecod/inc/defines.h
	ldecod/inc/elements.h
	ldecod/inc/erc_api.h
	ldecod/inc/erc_do.h
	ldecod/inc/erc_globals.h
	ldecod/inc/errorconcealment.h
	ldecod/inc/filehandle.h
	ldecod/inc/fmo.h
	ldecod/inc/global.h
	ldecod/inc/h264decoder.h
	ldecod/inc/header.h
	ldecod/inc/image.h
	ldecod/inc/intra16x16_pred.h
	ldecod/inc/intra4x4_pred.h
	ldecod/inc/intra8x8_pred.h
	ldecod/inc/leaky_bucket.h
	ldecod/inc/loopfilter.h
	ldecod/inc/loop_filter.h
	ldecod/inc/macroblock.h
	ldecod/inc/mbuffer.h
	ldecod/inc/mbuffer_mvc.h
	ldecod/inc/mb_prediction.h
	ldecod/inc/mc_prediction.h
	ldecod/inc/nalu.h
	ldecod/inc/output.h
	ldecod/inc/parset.h
	ldecod/inc/quant.h
	ldecod/inc/rtp.h
	ldecod/inc/sei.h
	ldecod/inc/transform8x8.h
	ldecod/inc/vlc.h
	lcommon/inc/blk_prediction.h
	lcommon/inc/config_common.h
	lcommon/inc/ctx_tables.h
	lcommon/inc/distortion.h
	lcommon/inc/enc_statistics.h
	lcommon/inc/fast_memory.h
	lcommon/inc/frame.h
	lcommon/inc/ifunctions.h
	lcommon/inc/img_io.h
	lcommon/inc/img_process.h
	lcommon/inc/img_process_types.h
	lcommon/inc/input.h
	lcommon/inc/io_image.h
	lcommon/inc/io_raw.h
	lcommon/inc/io_tiff.h
	lcommon/inc/io_video.h
	lcommon/inc/lagrangian.h
	lcommon/inc/mbuffer_common.h
	lcommon/inc/mb_access.h
	lcommon/inc/memalloc.h
	lcommon/inc/mv_prediction.h
	lcommon/inc/nalucommon.h
	lcommon/inc/parsetcommon.h
	lcommon/inc/quant_params.h
	lcommon/inc/report.h
	lcommon/inc/transform.h
	lcommon/inc/typedefs.h
	lcommon/inc/types.h
	lcommon/inc/vui_params.h
	lcommon/inc/win32.h
)

set( JM_NAME_SRC
	
	ldecod/src/annexb.c
	ldecod/src/biaridecod.c
	ldecod/src/block.c
	ldecod/src/cabac.c
	ldecod/src/configfile.c
	ldecod/src/context_ini.c
	ldecod/src/dec_statistics.c
	ldecod/src/erc_api.c
	ldecod/src/erc_do_i.c
	ldecod/src/erc_do_p.c
	ldecod/src/errorconcealment.c
	ldecod/src/filehandle.c
	ldecod/src/fmo.c
	ldecod/src/header.c
	ldecod/src/image.c
	ldecod/src/intra16x16_pred.c
	ldecod/src/intra16x16_pred_mbaff.c
	ldecod/src/intra16x16_pred_normal.c
	ldecod/src/intra4x4_pred.c
	ldecod/src/intra4x4_pred_mbaff.c
	ldecod/src/intra4x4_pred_normal.c
	ldecod/src/intra8x8_pred.c
	ldecod/src/intra8x8_pred_mbaff.c
	ldecod/src/intra8x8_pred_normal.c
	ldecod/src/intra_chroma_pred.c
	ldecod/src/intra_chroma_pred_mbaff.c
	ldecod/src/intra_pred_common.c
	ldecod/src/ldecod.c
	ldecod/src/leaky_bucket.c
	ldecod/src/loopFilter.c
	ldecod/src/loop_filter_mbaff.c
	ldecod/src/loop_filter_normal.c
	ldecod/src/macroblock.c
	ldecod/src/mbuffer.c
	ldecod/src/mbuffer_mvc.c
	ldecod/src/mb_access.c
	ldecod/src/mb_prediction.c
	ldecod/src/mb_read.c
	ldecod/src/mc_direct.c
	ldecod/src/mc_prediction.c
	ldecod/src/nal.c
	ldecod/src/nalu.c
	ldecod/src/output.c
	ldecod/src/parset.c
	ldecod/src/quant.c
	ldecod/src/read_comp_cabac.c
	ldecod/src/read_comp_cavlc.c
	ldecod/src/rtp.c
	ldecod/src/sei.c
	ldecod/src/transform8x8.c
	ldecod/src/vlc.c
	lcommon/src/blk_prediction.c
	lcommon/src/config_common.c
	lcommon/src/img_io.c
	lcommon/src/img_process.c
	lcommon/src/input.c
	lcommon/src/io_raw.c
	lcommon/src/io_tiff.c
	lcommon/src/mbuffer_common.c
	lcommon/src/memalloc.c
	lcommon/src/mv_prediction.c
	lcommon/src/nalucommon.c
	lcommon/src/parsetcommon.c
	lcommon/src/transform.c
	lcommon/src/win32.c
)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/bin/)

# Include directories
include_directories ("ldecod/inc")
include_directories ("lcommon/inc")
include_directories ("${PROJECT_SOURCE_DIR}/include")

add_executable( H264AnalysisTool ${NAME_SRC} ${JM_NAME_SRC} ${NAME_HEADERS} ${JM_NAME_HEADERS})

# OpenCV
find_package( OpenCV REQUIRED )
if (OpenCV_FOUND)
include_directories( ${OpenCV_INCLUDE_DIRS} )
target_link_libraries( H264AnalysisTool ${OpenCV_LIBS} )
endif( OpenCV_FOUND )
# zlib
find_package( ZLIB REQUIRED )
if ( ZLIB_FOUND )
    include_directories( ${ZLIB_INCLUDE_DIRS} )
    target_link_libraries( H264AnalysisTool ${ZLIB_LIBRARIES} )
endif( ZLIB_FOUND ) 
# winsock
if(WIN32)
    # target_link_libraries(H264AnalysisTool wsock32 ws2_32)
endif()

