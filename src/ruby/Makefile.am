INCLUDES = -I$(top_srcdir)/src -I$(top_srcdir)/src/ohcount -I$(RUBY_INC)
AM_LDFLAGS = -no-undefined -lpcre -lruby

all: ohcount.c

BUILT_SOURCES = $(srcdir)/ohcount.c
SWIG_SOURCES = ../swig/ohcount.i

lib_LTLIBRARIES = libohcount_ruby.la

# static library ../ohcount/liboh.a has all this stuff built;
# beats me how to trick libtool into using a static library!

libohcount_ruby_la_SOURCES = $(SWIG_SOURCES) \
../ohcount/detector.c               \
../ohcount/diff.c                   \
../ohcount/licenses.c               \
../ohcount/loc.c                    \
../ohcount/parsed_language.c        \
../ohcount/parser.c                 \
../ohcount/sourcefile.c             \
../hash/language_hash.c

libohcount_ruby_la_LDFLAGS = -module -bundle -dynamic -lruby -lpcre

ohcount.c : $(SWIG_SOURCES)
	swig -I$(top_srcdir)/src -ruby -o ohcount.c ../swig/ohcount.i
