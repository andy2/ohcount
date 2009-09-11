INCLUDES = -I$(top_srcdir)/src -I$(top_srcdir)/src/ohcount
AM_LDFLAGS = -no-undefined -lpcre

BUILT_SOURCES = ohcount.c
SWIG_SOURCES = ../swig/ohcount.i

pkgpython_PYTHON = ohcount.py
pkgpyexec_LTLIBRARIES = _ohcount.la
_ohcount_la_CFLAGS = $(SWIG_PYTHON_CFLAGS)
_ohcount_la_LDFLAGS = -module
#_ohcount_la_LIBADD = ../src/libproject.la

ohcount.c : $(SWIG_SOURCES)
	$(SWIG) $(SWIG_PYTHON_OPT) -o $@ $<

# static library ../ohcount/liboh.a has all this stuff built;
# beats me how to trick libtool into using a static library!

_ohcount_la_SOURCES = $(SWIG_SOURCES) ohcount.c   \
../ohcount/detector.c               \
../ohcount/diff.c                   \
../ohcount/licenses.c               \
../ohcount/loc.c                    \
../ohcount/parsed_language.c        \
../ohcount/parser.c                 \
../ohcount/sourcefile.c             \
../hash/language_hash.c
