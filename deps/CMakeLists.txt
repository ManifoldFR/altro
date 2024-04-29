
# ArduinoEigen
if (ALTRO_ENABLE_ARDUINO_LIB_INSTALL)
  list(APPEND CMAKE_MESSAGE_CONTEXT arduinoeigen)
  FetchContent_Declare(arduinoeigen
    GIT_REPOSITORY https://github.com/hideakitai/ArduinoEigen.git
    GIT_TAG 0.2.3
    )
  FetchContent_MakeAvailable(arduinoeigen)
  list(POP_BACK CMAKE_MESSAGE_CONTEXT)
endif()
