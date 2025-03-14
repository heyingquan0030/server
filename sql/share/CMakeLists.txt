# Copyright (c) 2006 MySQL AB, 2009, 2010 Sun Microsystems, Inc.
# Use is subject to license terms.
# 
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; version 2 of the License.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1335 USA

SET (dirs 
bulgarian
chinese
czech
danish
dutch
english
estonian
french
german
georgian
greek
hindi
hungarian
italian
japanese
korean
norwegian-ny
norwegian
polish
portuguese
romanian
russian
serbian
slovak
spanish
swahili
swedish
ukrainian
)

SET(files 
 errmsg-utf8.txt
)

INSTALL(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/charsets DESTINATION ${INSTALL_MYSQLSHAREDIR}
  COMPONENT Common PATTERN "languages.html" EXCLUDE
)

IF (NOT WITHOUT_SERVER)
  FOREACH (dir ${dirs})
   INSTALL(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/${dir}
    DESTINATION  ${INSTALL_MYSQLSHAREDIR} COMPONENT Server)
  ENDFOREACH()
  INSTALL(FILES ${files} DESTINATION ${INSTALL_MYSQLSHAREDIR} COMPONENT Server)
ENDIF()
