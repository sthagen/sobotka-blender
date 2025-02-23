# SPDX-License-Identifier: GPL-2.0-or-later

set(INC
  ../include
  ../uvedit
  ../../blenkernel
  ../../blenlib
  ../../blentranslation
  ../../bmesh
  ../../depsgraph
  ../../draw
  ../../functions
  ../../geometry
  ../../gpu
  ../../imbuf
  ../../makesdna
  ../../makesrna
  ../../nodes
  ../../render
  ../../windowmanager
  ../../../../intern/atomic
  ../../../../intern/clog
  ../../../../intern/eigen
  ../../../../intern/guardedalloc
  # RNA_prototypes.h
  ${CMAKE_BINARY_DIR}/source/blender/makesrna
)

set(SRC
  curves_sculpt_add.cc
  curves_sculpt_brush.cc
  curves_sculpt_comb.cc
  curves_sculpt_delete.cc
  curves_sculpt_density.cc
  curves_sculpt_grow_shrink.cc
  curves_sculpt_ops.cc
  curves_sculpt_pinch.cc
  curves_sculpt_puff.cc
  curves_sculpt_selection.cc
  curves_sculpt_selection_paint.cc
  curves_sculpt_slide.cc
  curves_sculpt_smooth.cc
  curves_sculpt_snake_hook.cc
  paint_canvas.cc
  paint_cursor.cc
  paint_curve.c
  paint_curve_undo.c
  paint_hide.c
  paint_image.cc
  paint_image_2d.c
  paint_image_2d_curve_mask.cc
  paint_image_ops_paint.cc
  paint_image_proj.cc
  paint_mask.cc
  paint_ops.c
  paint_stroke.c
  paint_utils.c
  paint_vertex.cc
  paint_vertex_color_ops.cc
  paint_vertex_proj.c
  paint_vertex_weight_ops.cc
  paint_vertex_weight_utils.c
  sculpt.cc
  sculpt_automasking.cc
  sculpt_boundary.c
  sculpt_brush_types.c
  sculpt_cloth.c
  sculpt_detail.c
  sculpt_dyntopo.cc
  sculpt_expand.cc
  sculpt_face_set.cc
  sculpt_filter_color.c
  sculpt_filter_mask.c
  sculpt_filter_mesh.c
  sculpt_geodesic.cc
  sculpt_mask_expand.c
  sculpt_mask_init.c
  sculpt_multiplane_scrape.c
  sculpt_ops.c
  sculpt_paint_color.c
  sculpt_paint_image.cc
  sculpt_pose.c
  sculpt_smooth.c
  sculpt_transform.c
  sculpt_undo.cc
  sculpt_uv.c

  curves_sculpt_intern.h
  curves_sculpt_intern.hh
  paint_intern.h
  sculpt_intern.h
)

set(LIB
  bf_blenkernel
  bf_blenlib
)

if(WITH_TBB)
  list(APPEND INC_SYS
    ${TBB_INCLUDE_DIRS}
  )
  add_definitions(-DWITH_TBB)
endif()

if(WIN32)
    add_definitions(-DNOMINMAX)
endif()

blender_add_lib(bf_editor_sculpt_paint "${SRC}" "${INC}" "${INC_SYS}" "${LIB}")

# RNA_prototypes.h
add_dependencies(bf_editor_sculpt_paint bf_rna)
