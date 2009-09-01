INCLUDES = -I$(top_srcdir)/src

noinst_LIBRARIES = liboh.a
liboh_a_SOURCES = detector.c diff.c licenses.c loc.c parsed_language.c parser.c sourcefile.c ../hash/language_hash.c

bin_PROGRAMS = ohcount
ohcount_SOURCES = ohcount.c
ohcount_LDADD = liboh.a -lpcre

