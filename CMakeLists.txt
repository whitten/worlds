cmake_minimum_required(VERSION 3.2)

project(WorldforgeWorlds)
include(GNUInstallDirs)


set(WORLDS_VERSION_MAJOR 0)
set(WORLDS_VERSION_MINOR 1)
set(WORLDS_VERSION_PATCH 0)

set(VERSION ${WORLDS_VERSION_MAJOR}.${WORLDS_VERSION_MINOR}.${WORLDS_VERSION_PATCH})

set(DESCRIPTION "A collection of worlds for the Worldforge system.")


install(DIRECTORY basic deeds mason DESTINATION ${CMAKE_INSTALL_FULL_DATADIR}/worldforge/worlds)

# Packaging

set(CPACK_PACKAGE_DESCRIPTION_SUMMARY ${DESCRIPTION})
set(CPACK_PACKAGE_VENDOR "Worldforge")
set(CPACK_PACKAGE_DESCRIPTION_FILE "${PROJECT_SOURCE_DIR}/Readme.md")
set(CPACK_RESOURCE_FILE_LICENSE "${PROJECT_SOURCE_DIR}/COPYING")
set(CPACK_PACKAGE_VERSION_MAJOR "${WORLDS_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${WORLDS_VERSION_MINOR}")
set(CPACK_PACKAGE_VERSION_PATCH "${WORLDS_VERSION_PATCH}")

set(CPACK_SOURCE_GENERATOR TBZ2 ZIP)

set(CPACK_SOURCE_PACKAGE_FILE_NAME "${PROJECT_NAME}-${VERSION}" CACHE INTERNAL "tarball basename")

set(CPACK_SOURCE_IGNORE_FILES
        # no hidden files
        "/\\\\..+$"
        "~$"
        )

include(CPack)
