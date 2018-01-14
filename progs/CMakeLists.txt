# Define this directory's flags:
SET(CMAKE_CXX_FLAGS  ${DIAG_FLAGS})

include_directories ( ${CMAKE_SOURCE_DIR}/include/diagnostic )
include_directories ( ${CMAKE_SOURCE_DIR}/include )

# Benchmarks
add_exe_and_link ( vdtPerfBenchmark vdtPerfBenchmark.cpp ${LIBTIMING})
add_exe_and_link ( vdtArithmBenchmark vdtArithmBenchmark.cpp None)
add_exe_and_link ( vdtArithmComparison vdtArithmComparison.cpp None)

INSTALL ( DIRECTORY ${CMAKE_BINARY_DIR}/bin/
          FILE_PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_WRITE GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
          DESTINATION bin
)
