include(FetchContent)

set(FETCHCONTENT_BASE_DIR "${CMAKE_CURRENT_SOURCE_DIR}")

set(ALGOIM_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/algoim-src")
set(ALGOIM_INSTALL_DIR "${CMAKE_CURRENT_SOURCE_DIR}/algoim-install")

FetchContent_Declare(
    algoim
    GIT_REPOSITORY  https://github.com/algoim/algoim.git
)
# download version of October 2nd, 2019
FetchContent_MakeAvailable(algoim)