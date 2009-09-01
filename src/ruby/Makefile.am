INCLUDES = -I$(top_srcdir)/src -I$(RUBY_INC)
AM_LDFLAGS = -no-undefined -lpcre -lruby

all: ohcount.c

ohcount.c : ohcount.i
	swig -I$(top_srcdir)/src -ruby -o ohcount.c ohcount.i

lib_LTLIBRARIES = libohcount.la

# static library ../ohcount/liboh.a has all this stuff built;
# beats me how to trick libtool to use a static library!

libohcount_la_SOURCES = ohcount.c   \
../ohcount/detector.c               \
../ohcount/diff.c                   \
../ohcount/licenses.c               \
../ohcount/loc.c                    \
../ohcount/parsed_language.c        \
../ohcount/parser.c                 \
../ohcount/sourcefile.c             \
../hash/language_hash.c
