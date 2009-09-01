AC_INIT([ohcount], [3.0], [support@ohloh.net])

AC_CONFIG_MACRO_DIR([m4])
AM_INIT_AUTOMAKE

# arguments

AC_ARG_WITH(ruby,
  AC_HELP_STRING([--with-ruby], [enable Ruby bindings]),
  [],
  [with_ruby=no])

# programs

AC_PROG_CC
AC_PROG_LIBTOOL

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

# config

AC_CONFIG_FILES([
    Makefile
    src/Makefile
    src/hash/Makefile
    src/parsers/Makefile
    src/ohcount/Makefile
    test/unit/Makefile
])

if test "$with_ruby" != "no"; then
AC_CONFIG_FILES([
    src/ruby/Makefile
    test/unit/ruby/Makefile
])
fi

AC_OUTPUT

