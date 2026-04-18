# Создаем библиотеку. Пути пишем ОТНОСИТЕЛЬНО этого файла.
# Так как файлы лежат в папке src рядом с этим CMakeLists, пишем src/...
add_library(resource_core
        src/FileHandle.cpp
        src/ResourceManager.cpp
        include/lab4/resource/ResourceError.hpp
        include/lab4/resource/ResourceManager.hpp
        include/lab4/resource/FileHandle.hpp
)

# Указываем, где искать заголовки. 
# Они лежат в папке include рядом с этим файлом.
target_include_directories(resource_core PUBLIC include)

# Подключаем варнинги и санитайзеры, которые мы создали в корне
target_link_libraries(resource_core PRIVATE project_warnings)

if(TARGET project_sanitizers)
        target_link_libraries(resource_core PRIVATE project_sanitizers)
endif()