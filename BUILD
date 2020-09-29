# Copyright 2020 Google LLC
# 
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
# Supporting infrastructure for implementing and testing PINS.

# load("//tools/build_defs/testing:bzl_library.bzl", "bzl_library")

package(
    default_visibility = ["//visibility:public"],
    licenses = ["notice"],
)

exports_files(["LICENSE"])

# copybara:insert_begin(For format.sh script)
# load("@com_github_bazelbuild_buildtools//buildifier:def.bzl", "buildifier")
#
# buildifier(
#     name = "buildifier",
# )
# copybara:insert_end

# Files needed to run expect.
filegroup(
    name = "everything",
    srcs = [
        "pkgIndex.tcl",
        ":expect",
        "@tcl//:main",
    ],
)

common_copts = [
    "-w",
    "-DDFLT_STTY=\\\"sane\\\"",
    "-DEXECSCRIPTDIR=\\\"/usr/local/lib/expect5.44.1.15\\\"",
    "-DHAVE_GMTIME_R=1",
    "-DHAVE_INTTYPES_H=1",
    "-DHAVE_LIMITS_H=1",
    "-DHAVE_LOCALTIME_R=1",
    "-DHAVE_LONG_FILE_NAMES=1",
    "-DHAVE_MEMCPY=1",
    "-DHAVE_MEMMOVE=1",
    "-DHAVE_MEMORY_H=1",
    "-DHAVE_OPENPTY=1",
    "-DHAVE_PTMX=1",
    "-DHAVE_SIGLONGJMP=1",
    "-DHAVE_STDINT_H=1",
    "-DHAVE_STDLIB_H=1",
    "-DHAVE_STRCHR=1",
    "-DHAVE_STRFTIME=1",
    "-DHAVE_STRINGS_H=1",
    "-DHAVE_STRING_H=1",
    "-DHAVE_STROPTS_H=1",
    "-DHAVE_STRUCT_TM_TM_ZONE=1",
    "-DHAVE_SV_TIMEZONE=1",
    "-DHAVE_SYSCONF=1",
    "-DHAVE_SYSMACROS_H=1",
    "-DHAVE_SYS_FCNTL_H=1",
    "-DHAVE_SYS_PARAM_H=1",
    "-DHAVE_SYS_SELECT_H=1",
    "-DHAVE_SYS_STAT_H=1",
    "-DHAVE_SYS_TIME_H=1",
    "-DHAVE_SYS_TYPES_H=1",
    "-DHAVE_TCSETATTR=1",
    "-DHAVE_TERMIO=1",
    "-DHAVE_TERMIOS=1",
    "-DHAVE_TIMEZONE=1",
    "-DHAVE_TIMEZONE_VAR=1",
    "-DHAVE_TM_GMTOFF=1",
    "-DHAVE_TM_ZONE=1",
    "-DHAVE_UNISTD_H=1",
    "-DPACKAGE_BUGREPORT=\\\"\\\"",
    "-DPACKAGE_NAME=\\\"expect\\\"",
    "-DPACKAGE_STRING=\\\"expect\\ 5.44.1.15\\\"",
    "-DPACKAGE_TARNAME=\\\"expect\\\"",
    "-DPACKAGE_VERSION=\\\"5.44.1.15\\\"",
    "-DPOSIX=1",
    "-DRETSIGTYPE=void",
    "-DSCRIPTDIR=\\\"/usr/local/lib/expect5.44.1.15\\\"",
    "-DSELECT_MASK_TYPE=fd_set",
    "-DSETPGRP_VOID=1",
    "-DSTDC_HEADERS=1",
    "-DSTTY_BIN=\\\"/bin/stty\\\"",
    "-DTCL_DEBUGGER",
    "-DTCL_WIDE_INT_IS_LONG=1",
    "-DTIME_WITH_SYS_TIME=1",
    "-DUSE_NON_CONST",
    "-DUSE_TCL_STUBS=1",
    "-DWNOHANG_BACKUP_VALUE=1",
    "-D_LARGEFILE64_SOURCE=1",
    "-D_REENTRANT=1",
    "-D_THREAD_SAFE=1",
    "-DNO_UNION_WAIT=1",
]

cc_binary(
    name = "expect",
    srcs = ["exp_main_exp.c"],
    copts = common_copts,
    linkopts = ["-lutil"],  # Needed for openpty().
    deps = [
        ":libexpect",
        "@tcl//:main",
    ],
)

cc_library(
    name = "libexpect",
    srcs = [
        "Dbg.c",
        "exp_chan.c",
        "exp_clib.c",
        "exp_closetcl.c",
        "exp_command.c",
        "exp_command.h",
        "exp_console.c",
        "exp_event.c",
        "exp_event.h",
        "exp_glob.c",
        "exp_int.h",
        "exp_inter.c",
        "exp_log.c",
        "exp_log.h",
        "exp_main_sub.c",
        "exp_memmove.c",
        "exp_prog.h",
        "exp_pty.c",
        "exp_pty.h",
        "exp_regexp.c",
        "exp_select.c",
        "exp_strf.c",
        "exp_trap.c",
        "exp_tstamp.h",
        "exp_tty.c",
        "exp_tty.h",
        "exp_tty_comm.c",
        "exp_tty_in.h",
        "exp_win.c",
        "exp_win.h",
        "expect.c",
        "expect.h",
        "expect_comm.h",
        "pty_termios.c",
        "tcldbg.h",
        "tcldbgcf.h",
    ],
    hdrs = [
        "expect_tcl.h",
        "retoglob.c",
    ],
    copts = common_copts,
    visibility = ["//visibility:public"],
    deps = ["@com_tcl//:tcl"],
)
