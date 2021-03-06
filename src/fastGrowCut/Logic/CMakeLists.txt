project(vtkSlicer${MODULE_NAME}ModuleLogic)

set(KIT ${PROJECT_NAME})

set(${KIT}_EXPORT_DIRECTIVE "VTK_SLICER_${MODULE_NAME_UPPER}_MODULE_LOGIC_EXPORT")

set(${KIT}_INCLUDE_DIRECTORIES
  )

set(FASTGROWCUT_SRCS
  fibheap.cpp
  fibheap.h
  utilities.h
  FastGrowCutSegmenter.h
  FastGrowCutSegmenter.hxx
  KSandbox.h
  )

set(FASTGROWCUT_LIBS
${ITK_LIBRARIES}
)


add_library(FastGrowCutLogic STATIC ${FASTGROWCUT_SRCS})
target_link_libraries(FastGrowCutLogic ${FASTGROWCUT_LIBS})

set(${KIT}_SRCS
  vtkSlicer${MODULE_NAME}Logic.cxx
  vtkSlicer${MODULE_NAME}Logic.h
  vtkFastGrowCut.cxx
  vtkFastGrowCut.h
  )

set(${KIT}_TARGET_LIBRARIES
  #${ITK_LIBRARIES}
  FastGrowCutLogic
  )

#-----------------------------------------------------------------------------
SlicerMacroBuildModuleLogic(
  NAME ${KIT}
  EXPORT_DIRECTIVE ${${KIT}_EXPORT_DIRECTIVE}
  INCLUDE_DIRECTORIES ${${KIT}_INCLUDE_DIRECTORIES}
  SRCS ${${KIT}_SRCS}
  TARGET_LIBRARIES ${${KIT}_TARGET_LIBRARIES}
  )
