# Define the package version numbers, bug reporting link, project homepage.
m4_define([HASHIDS_VERSION_MAJOR_], [1])
m4_define([HASHIDS_VERSION_MINOR_], [1])
m4_define([HASHIDS_VERSION_PATCH_], [4])
m4_define([HASHIDS_VERSION_STRING_], [HASHIDS_VERSION_MAJOR_.HASHIDS_VERSION_MINOR_.HASHIDS_VERSION_PATCH_])
m4_define([HASHIDS_BUGREPORT_URL_], [https://github.com/tzvetkoff/hashids.c/issues])
m4_define([HASHIDS_PROJECT_URL_], [https://github.com/tzvetkoff/hashids.c])

# Initialize autoconf & automake.
AC_PREREQ(2.59)
AC_INIT([hashids], [HASHIDS_VERSION_STRING_], [HASHIDS_BUGREPORT_URL_], [hashids], [HASHIDS_PROJECT_URL_])
AC_CONFIG_AUX_DIR([config])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([m4])
AM_INIT_AUTOMAKE([1.9 foreign])

# Checks for programs.
AC_PROG_CC()
AC_PROG_CPP()
AC_PROG_INSTALL()
AC_PROG_LN_S()
AC_PROG_MAKE_SET()

# Libtool.
LT_INIT()

# GLibC's math.
AC_CHECK_LIB([m], [ceil], [LIBM="-lm"])
AC_SUBST([LIBM])

# Debug.
AC_ARG_ENABLE([debug], AS_HELP_STRING([--enable-debug], [Enable debugging @<:@default=no@:>@.]), [
  case "${enableval}" in
    yes) HASHIDS_DEBUG="1"; CFLAGS="${CFLAGS} -g -fsanitize=address -fno-omit-frame-pointer";;
    no)  HASHIDS_DEBUG="0";;
    *)   AC_MSG_ERROR(["bad value ${enableval} for feature --enable-debug"]);;
  esac
], [
  HASHIDS_DEBUG="0"
])
AM_CONDITIONAL([DEBUG], [test "x${HASHIDS_DEBUG}" = "x1"])
AC_DEFINE_UNQUOTED([DEBUG], [${HASHIDS_DEBUG}], [Debug mode.])

# Makefiles.
AC_CONFIG_FILES([Makefile src/Makefile])

# Le grand finale.
AC_OUTPUT()
