cmake_minimum_required(VERSION 3.5)
project(sound_play)

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)
find_package(audio_common_msgs REQUIRED)
find_package(action_msgs REQUIRED)

ament_python_install_package(sound_play)

install(PROGRAMS
        sound_play/is_speaking.py
        sound_play/playbuiltin.py
        sound_play/play.py
        sound_play/say.py
        sound_play/shutup.py
        sound_play/soundplay_node.py
        sound_play/libsoundplay.py
  # scripts/test.py
  # scripts/test_actionlib_client.py
  DESTINATION lib/${PROJECT_NAME}
)
install(PROGRAMS
        sound_play/libsoundplay.py
        DESTINATION share/${PROJECT_NAME}
        )

install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION include/${PROJECT_NAME}
)

install(DIRECTORY launch
  DESTINATION share/${PROJECT_NAME}
)

install(DIRECTORY sounds
  DESTINATION share/${PROJECT_NAME}
)


ament_package()
