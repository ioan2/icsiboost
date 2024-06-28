# Copyright (C) (2007) (Benoit Favre) <favre@icsi.berkeley.edu>
#
# This program is free software; you can redistribute it and/or 
# modify it under the terms of the GNU Lesser General Public License 
# as published by the Free Software Foundation; either 
# version 2 of the License, or (at your option) any later 
# version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.

AC_PREREQ([2.71])
AC_INIT([icsiboost],[0.3c],[favre@icsi.berkeley.edu])
#AC_CONFIG_SRCDIR([src/icsiboost.c])
AM_INIT_AUTOMAKE()
AC_CONFIG_HEADERS([config.h])

case `uname` in
	*Darwin*)
	CFLAGS="-fnested-functions -I/opt/local/include -L/opt/local/lib"
	;;
	*SunOS*)
	CFLAGS="-I/usr/include/pcre"
	;;
esac
# Checks for programs.
AC_PROG_CC
AC_PROG_CXX

# Checks for libraries.
# FIXME: Replace `main' with a function in `-lm':
AC_CHECK_LIB([m], [main])
# FIXME: Replace `main' with a function in `-lpcre':
AC_CHECK_LIB([pcre], [main])
# FIXME: Replace `main' with a function in `-lpthread':
AC_CHECK_LIB([pthread], [main])
# FIXME: Replace `main' with a function in `-lz':
AC_CHECK_LIB([z], [main])

# Checks for header files.
m4_warn([obsolete],
[The preprocessor macro `STDC_HEADERS' is obsolete.
  Except in unusual embedded environments, you can safely include all
  ISO C90 headers unconditionally.])dnl
# Autoupdate added the next two lines to ensure that your configure
# script's behavior did not change.  They are probably safe to remove.
AC_CHECK_INCLUDES_DEFAULT
AC_PROG_EGREP

AC_HEADER_SYS_WAIT
AC_CHECK_HEADERS([fcntl.h stdint.h stdlib.h string.h unistd.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST
AC_C_INLINE
AC_TYPE_OFF_T
AC_TYPE_SIZE_T

# Checks for library functions.
AC_FUNC_FORK
AC_FUNC_FSEEKO
AC_FUNC_MEMCMP
AC_FUNC_MMAP
m4_warn([obsolete],
[your code may safely assume C89 semantics that RETSIGTYPE is void.
Remove this warning and the `AC_CACHE_CHECK' when you adjust the code.])dnl
AC_CACHE_CHECK([return type of signal handlers],[ac_cv_type_signal],[AC_COMPILE_IFELSE(
[AC_LANG_PROGRAM([#include <sys/types.h>
#include <signal.h>
],
		 [return *(signal (0, 0)) (0) == 1;])],
		   [ac_cv_type_signal=int],
		   [ac_cv_type_signal=void])])
AC_DEFINE_UNQUOTED([RETSIGTYPE],[$ac_cv_type_signal],[Define as the return type of signal handlers
		    (`int' or `void').])

AC_FUNC_STAT
AC_FUNC_STRTOD
AC_CHECK_FUNCS([dup2 memmove memset munmap regcomp sqrt strdup strerror strtol])

# generate version information
#svn info|awk 'BEGIN{print "#ifndef _VERSION_H_\n#define _VERSION_H_\n#define SVN_INFO \\"}{print "\"  " $0 "\\n\" \\"}END{print "\"\"\n#endif"}' > $SOURCE_DIR/version.h

AC_CONFIG_FILES([Makefile
                 src/Makefile])
AC_OUTPUT
