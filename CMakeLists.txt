# CMakeList.txt: проект CMake для Search_Engine_proba; включите исходный код и определения,
# укажите здесь логику для конкретного проекта.
#
cmake_minimum_required (VERSION 3.8)

# Включение горячей перезагрузки для компиляторов MSVC, если поддерживается.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

set(JSON_BuildTests OFF CACHE INTERNAL "")
add_subdirectory(nlohmann_json)

project ("Search_Engine_proba")





# Добавьте источник в исполняемый файл этого проекта.
add_executable (Search_Engine_proba "Search_Engine_proba.cpp" "Search_Engine_proba.h" "include/ConverterJSON.h" 
"include/InvertedIndex.h" "include/SearchServer.h" "src/ConverterJSON.cpp" "src/InvertedIndex.cpp" "src/SearchServer.cpp")

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET Search_Engine_proba PROPERTY CXX_STANDARD 20)
endif()



target_link_libraries(Search_Engine_proba PRIVATE nlohmann_json::nlohmann_json)
# TODO: Добавьте тесты и целевые объекты, если это необходимо.
