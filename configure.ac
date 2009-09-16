AC_INIT(ohcount, 3.0)

AC_CONFIG_MACRO_DIR([m4])
AM_INIT_AUTOMAKE

AM_PATH_PYTHON(2.6.2)
#AM_PATH_RUBY
AC_PROG_SWIG(1.3.21)
AX_SWIG_PYTHON

# arguments

AC_ARG_WITH(ruby,
  AC_HELP_STRING([--with-ruby], [enable Ruby bindings]),
  [],
  [with_ruby=no])

AC_ARG_WITH(python,
  AC_HELP_STRING([--with-python], [enable Python bindings]),
  [],
  [with_python=no])

# programs

AC_PROG_CC
AC_DISABLE_STATIC
AC_PROG_SWIG
SWIG_ENABLE_CXX
SWIG_YTHON
SWIG_RUBY
AC_PROG_LIBTOOL
LT_INIT([disable-static])

AC_HEADER_STDC

AC_CHECK_HEADER(pcre.h, , [
   AC_MSG_ERROR([header pcre.h not found - install package libpcre-dev])
])

AC_CHECK_PROG(GPERF, gperf, gperf)
AS_IF([test -z "$GPERF"], [AC_MSG_ERROR([gperf is required to build the parsers])])

AC_CHECK_PROG(RAGEL, ragel, ragel)
AS_IF([test -z "$RAGEL"], [AC_MSG_ERROR([ragel is required to build the parsers])])

if test "$with_ruby" != "no"; then
    AC_CHECK_PROG(RUBY, ruby, ruby)
    AS_IF([test -z "$RUBY"], [AC_MSG_ERROR([ruby is required to build ruby bindings])])

    AC_CHECK_PROG(SWIG, swig, swig)
    AS_IF([test -z "$SWIG"], [AC_MSG_ERROR([swig is required to build ruby bindings])])

    [RUBY_INC=`$RUBY -rrbconfig -e 'puts Config::CONFIG["rubyhdrdir"] || Config::CONFIG["archdir"]'`]
    [RUBY_ARCH=`$RUBY -rmkmf -e 'print Config::expand(CONFIG["arch"])'`]

    AC_SUBST(RUBY_INC)
    AC_SUBST(RUBY_ARCH)

    RUBY_SUBDIRS="src/ruby test/unit/ruby"
    AC_SUBST(RUBY_SUBDIRS)
fi

if test "$with_python" != "no"; then
    AC_CHECK_PROG(PYTHON, python, python)
    AS_IF([test -z "$PYTHON"], [AC_MSG_ERROR([python is required to build python bindings])])

    AC_CHECK_PROG(SWIG, swig, swig)
    AS_IF([test -z "$SWIG"], [AC_MSG_ERROR([swig is required to build python bindings])])

    PYTHON_SUBDIRS="src/python test/unit/python"
    AC_SUBST(PYTHON_SUBDIRS)
fi


# config

AC_CONFIG_FILES([
    Makefile
    src/Makefile
    src/hash/Makefile
    src/parsers/Makefile
    src/ohcount/Makefile
    test/unit/Makefile
    src/ruby/Makefile
    test/unit/ruby/Makefile
    src/python/Makefile
    test/unit/python/Makefile
])

AC_OUTPUT
