#!/bin/bash

RAGEL = ragel

.PHONY : all

all : 	actionscript.h ada.h assembler.h autoconf.h automake.h \
	awk.h bat.h blitzmax.h boo.h c.h classic_basic.h clearsilver.h \
	clearsilverhtml.h cmake.h common.h css.h cs_aspx.h d.h dcl.h \
	dylan.h ebuild.h eiffel.h erlang.h exheres.h factor.h fortranfixed.h \
	fortranfree.h glsl.h groovy.h haml.h haskell.h haxe.h html.h idl_pvwave.h \
	java.h javascript.h jsp.h limbo.h lisp.h lua.h makefile.h matlab.h \
	metafont.h metapost.h metapost_with_tex.h mxml.h nix.h objective_c.h \
	objective_j.h ocaml.h octave.h pascal.h perl.h php.h phphtml.h \
	pike.h python.h r.h rexx.h rhtml.h ruby.h scala.h scilab.h \
	shell.h smalltalk.h sql.h stratego.h structured_basic.h tcl.h \
	tex.h vb_aspx.h vhdl.h vim.h visual_basic.h xaml.h xml.h xmlschema.h \
	xslt.h

clean:
	rm -f *.h *.tmp *.xml

.rl.h:
	./compile $<
