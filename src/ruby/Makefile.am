INCLUDES = -I$(top_srcdir)/src -I$(top_srcdir)/src/ohcount -I$(RUBY_INC)
AM_LDFLAGS = -no-undefined -lpcre -lruby

all: ohcount.c

ohcount.c : ../swig/ohcount.i
	swig -I$(top_srcdir)/src -ruby -o ohcount.c ../swig/ohcount.i

lib_LTLIBRARIES = libohcount_ruby.la

# static library ../ohcount/liboh.a has all this stuff built;
# beats me how to trick libtool into using a static library!

libohcount_ruby_la_SOURCES = ohcount.c   \
../ohcount/detector.c               \
../ohcount/diff.c                   \
../ohcount/licenses.c               \
../ohcount/loc.c                    \
../ohcount/parsed_language.c        \
../ohcount/parser.c                 \
../ohcount/sourcefile.c             \
../hash/language_hash.c
