#
#   Copyright © 2009-2017 The Regents of the University of California.
#   All Rights Reserved.
#
#   Redistribution and use in source and binary forms, with or without
#   modification, are permitted provided that the following conditions are met:
#   •   Redistributions of source code must retain the above copyright notice,
#       this list of conditions and the following disclaimer.
#   •   Redistributions in binary form must reproduce the above copyright notice,
#       this list of conditions and the following disclaimer in the documentation
#       and/or other materials provided with the distribution.
#   •   None of the names of any campus of the University of California, the name
#       "The Regents of the University of California," or the names of any of its
#       contributors may be used to endorse or promote products derived from this
#       software without specific prior written permission.
#
#   THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
#   ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
#   WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED.
#   IN NO EVENT SHALL THE COPYRIGHT HOLDERS OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT,
#   INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT
#   NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR
#   PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
#   WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
#   ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY
#   OF SUCH DAMAGE.
#

#
#   $URL$
#   $Rev$
#   $Author$
#   $Date$
#

cmake_minimum_required(VERSION 2.4)

if(COMMAND cmake_policy)
    cmake_policy(SET CMP0003 NEW)
endif(COMMAND cmake_policy)


PROJECT(GE_console)

SET(CMAKE_VERBOSE_MAKEFILE TRUE)

ADD_CUSTOM_TARGET(
    Name ALL
    COMMAND installer 
    WORKING_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}
)

SET( COMPONENTS
    svk/bin
    svk/lib 
    svk/data
    svk/packages
)

FOREACH( ITEM ${COMPONENTS} )     
    INSTALL( 
        DIRECTORY ${ITEM}
        DESTINATION console
        #DIRECTORY_PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_WRITE GROUP_EXECUTE WORLD_READ WORLD_WRITE WORLD_EXECUTE 
        USE_SOURCE_PERMISSIONS
        PATTERN ".svn" EXCLUDE
        PATTERN ".git" EXCLUDE
    )
ENDFOREACH( ITEM )


