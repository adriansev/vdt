# Auto generate the code for the vector signatures and if needed preload

# Generate the code for the lib
if (PRELOAD)
set (SIGGENOPTS  " -p")
else()
set (SIGGENOPTS  " ")
endif()
EXEC_PROGRAM ("cd src;python ${CMAKE_SOURCE_DIR}/src/signatures_generator.py ${SIGGENOPTS} -o ${CMAKE_SOURCE_DIR}/src;cd -")

#generare Vc wrapper and config file
if(USE_VC)
  EXEC_PROGRAM ("cd src;python vc_wrapper_generator.py;cd -")
endif(USE_VC)
configure_file( ${INC_DIR}/vdt/externalLibcfg.h.cmake ${INC_DIR}/vdt/externalLibcfg.h)
