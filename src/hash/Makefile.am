.PHONY : all
all : \
	language_hash.c extension_hash.h filename_hash.h disambiguatefunc_hash.h \
	cppheader_hash.h parser_hash.h option_hash.h

clean:
	rm -f *.h *.c

language_hash.c : languages.gperf
	$(GPERF) -L ANSI-C -E -D -K key -H ohcount_hash_language -N ohcount_hash_language_from_name -t languages.gperf > language_hash.c

extension_hash.h : extensions.gperf
	$(GPERF) -L ANSI-C -E -D -K key -H ohcount_hash_extension -N ohcount_hash_language_from_ext -t extensions.gperf > extension_hash.h

filename_hash.h : filenames.gperf
	$(GPERF) -L ANSI-C -E -D -K key -H ohcount_hash_filename -N ohcount_hash_language_from_filename -t filenames.gperf > filename_hash.h

disambiguatefunc_hash.h : disambiguatefuncs.gperf
	$(GPERF) -L ANSI-C -E -D -K key -H ohcount_hash_disambiguatefunc -N ohcount_hash_disambiguate_func_from_id -t disambiguatefuncs.gperf > disambiguatefunc_hash.h

cppheader_hash.h : cppheaders.gperf
	$(GPERF) -L ANSI-C -E -D -K key -H ohcount_hash_cppheader -N ohcount_hash_is_cppheader -t cppheaders.gperf > cppheader_hash.h

parser_hash.h : parsers.gperf
	$(GPERF) -L ANSI-C -E -D -K key -H ohcount_hash_parser -N ohcount_hash_parser_from_language -t parsers.gperf > parser_hash.h

option_hash.h : options.gperf
	$(GPERF) -L ANSI-C -E -D -K key -H ohcount_hash_options -N ohcount_hash_command_from_flag -t options.gperf > option_hash.h

