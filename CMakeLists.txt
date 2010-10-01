# Copyright (C) 2007-2009 LuaDist.
# Created by Peter Kapec
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

PROJECT(lsqlite3 C)
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
INCLUDE(dist.cmake)

# Find SQLite3
FIND_PACKAGE(SQLite3 REQUIRED)
INCLUDE_DIRECTORIES (${SQLITE3_INCLUDE_DIRS})

# Create lsqlite module
ADD_LUA_MODULE(lsqlite3 lsqlite3.c lsqlite3.def)
TARGET_LINK_LIBRARIES(lsqlite3 ${SQLITE3_LIBRARIES})

# install lsqlite
INSTALL(TARGETS lsqlite3 DESTINATION ${INSTALL_CMOD})
INSTALL(FILES HISTORY README DESTINATION ${INSTALL_DATA})
INSTALL(DIRECTORY doc/ DESTINATION ${INSTALL_DOC})
INSTALL(FILES lunit.lua test.lua tests-sqlite3.lua  DESTINATION ${INSTALL_TEST})
INSTALL(DIRECTORY examples/ DESTINATION ${INSTALL_EXAMPLE})
