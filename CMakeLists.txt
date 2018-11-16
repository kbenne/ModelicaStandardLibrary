
project( ModelicaStandardLibrary C )

set ( ModelicaExternalC_SRC
  Modelica/Resources/C-Sources/ModelicaFFT.c
  Modelica/Resources/C-Sources/ModelicaInternal.c
  Modelica/Resources/C-Sources/ModelicaRandom.c
  Modelica/Resources/C-Sources/ModelicaStrings.c
)

if ( WIN32 )
  list( ADD ModelicaExternalC_SRC Modelica/Resources/C-Sources/win32_dirent.c )
endif()

add_library ( ModelicaExternalC
  ${ModelicaExternalC_SRC}
)

target_include_directories(ModelicaExternalC
  PUBLIC 
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/Modelica/Resources/C-Sources/>
  $<INSTALL_INTERFACE:include/>
)

install(TARGETS ModelicaExternalC EXPORT ModelicaStandardLibrary 
  RUNTIME DESTINATION bin
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
)

add_library ( ModelicaIO
  Modelica/Resources/C-Sources/ModelicaIO.c
)

target_include_directories(ModelicaIO
  PUBLIC 
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/Modelica/Resources/C-Sources/>
  $<INSTALL_INTERFACE:include/>
)

install(TARGETS ModelicaIO EXPORT ModelicaStandardLibrary 
  RUNTIME DESTINATION bin
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
)

add_library ( ModelicaMatIO
  Modelica/Resources/C-Sources/ModelicaMatIO.c
  Modelica/Resources/C-Sources/snprintf.c
)

target_include_directories(ModelicaMatIO
  PUBLIC 
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/Modelica/Resources/C-Sources/>
  $<INSTALL_INTERFACE:include/>
)

install(TARGETS ModelicaMatIO EXPORT ModelicaStandardLibrary 
  RUNTIME DESTINATION bin
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
)

add_library ( ModelicaStandardTables
  Modelica/Resources/C-Sources/ModelicaStandardTables.c
  Modelica/Resources/C-Sources/ModelicaStandardTablesUsertab.c
)

target_include_directories(ModelicaStandardTables 
  PUBLIC 
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/Modelica/Resources/C-Sources/>
  $<INSTALL_INTERFACE:include/>
)

install(TARGETS ModelicaStandardTables EXPORT ModelicaStandardLibrary 
  RUNTIME DESTINATION bin
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
)

add_library ( zlib
  Modelica/Resources/C-Sources/zlib//adler32.c
  Modelica/Resources/C-Sources/zlib//compress.c
  Modelica/Resources/C-Sources/zlib//crc32.c
  Modelica/Resources/C-Sources/zlib//deflate.c
  Modelica/Resources/C-Sources/zlib//gzclose.c
  Modelica/Resources/C-Sources/zlib//gzlib.c
  Modelica/Resources/C-Sources/zlib//gzread.c
  Modelica/Resources/C-Sources/zlib//gzwrite.c
  Modelica/Resources/C-Sources/zlib//infback.c
  Modelica/Resources/C-Sources/zlib//inffast.c
  Modelica/Resources/C-Sources/zlib//inflate.c
  Modelica/Resources/C-Sources/zlib//inftrees.c
  Modelica/Resources/C-Sources/zlib//trees.c
  Modelica/Resources/C-Sources/zlib//uncompr.c
  Modelica/Resources/C-Sources/zlib//zutil.c
)

target_include_directories(zlib 
  PUBLIC 
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/Modelica/Resources/C-Sources/zlib/>
  $<INSTALL_INTERFACE:include/zlib/>
)

install(TARGETS zlib EXPORT ModelicaStandardLibrary 
  RUNTIME DESTINATION bin
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
)

install(EXPORT ModelicaStandardLibrary DESTINATION lib/ModelicaStandardLibrary)


