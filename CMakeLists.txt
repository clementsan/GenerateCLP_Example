PROJECT(MAXFILTER)

FIND_PACKAGE(ITK REQUIRED)
IF(ITK_FOUND)
  INCLUDE(${USE_ITK_FILE})
ELSE(ITK_FOUND)
  MESSAGE(FATAL_ERROR "ITK not found. Please set ITK_DIR")
ENDIF(ITK_FOUND)

FIND_PACKAGE(GenerateCLP REQUIRED)
IF(GenerateCLP_FOUND)
  INCLUDE(${GenerateCLP_USE_FILE})
ELSE(ITK_FOUND)
  MESSAGE(FATAL_ERROR "GenerateCLP not found. Please set GenerateCLP_DIR")
ENDIF(GenerateCLP_FOUND)

SET(CXX_FILES 
  MaxFilter.cxx
)


LINK_LIBRARIES(${ITK_LIBRARIES})

GENERATECLP(MaxFilter.cxx MaxFilter.xml)

ADD_EXECUTABLE(MAXFILTER ${CXX_FILES} ${MaxFilter_SOURCE} )

