# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.20.0)

if (NOT DEFINED ENV{BSIM_COMPONENTS_PATH})
  message(FATAL_ERROR "This test requires the BabbleSim simulator. Please set\
 the  environment variable BSIM_COMPONENTS_PATH to point to its components \
 folder. More information can be found in\
 https://babblesim.github.io/folder_structure_and_env.html")
endif()

find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(bsim_test_l2cap_split_tester)

target_sources(app PRIVATE src/main.c)

zephyr_include_directories(
  ../common/
  ${ZEPHYR_BASE}/subsys/bluetooth/common/
  $ENV{BSIM_COMPONENTS_PATH}/libUtilv1/src/
  $ENV{BSIM_COMPONENTS_PATH}/libPhyComv1/src/
  )
