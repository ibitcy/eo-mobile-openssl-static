#
# Copyright (C) 2020 The Android Open Source Project
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

cmake_minimum_required(VERSION 3.6)
project(openssl LANGUAGES CXX)


add_library(crypto SHARED)

add_library(ssl SHARED)

#set_target_properties(
#        openssl::crypto
#        PROPERTIES
#        INTERFACE_INCLUDE_DIRECTORIES "${include}"
#        IMPORTED_LINK_INTERFACE_LANGUAGES "C"
#)
#
#set_target_properties(
#        openssl::ssl
#        PROPERTIES
#        INTERFACE_INCLUDE_DIRECTORIES "${include}"
#        IMPORTED_LINK_INTERFACE_LANGUAGES "C"
#)

#target_include_directories(
#        include
#)

#target_link_libraries(
#        openssl::crypto
#        openssl::ssl
#)


set_target_properties(crypto PROPERTIES LINKER_LANGUAGE CXX)

set_target_properties(ssl PROPERTIES LINKER_LANGUAGE CXX)
