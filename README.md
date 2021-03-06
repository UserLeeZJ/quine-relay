# Quine Relay

[![Build Status](https://travis-ci.org/mame/quine-relay.svg?branch=laboratory)](https://travis-ci.org/mame/quine-relay)

## What this is

This is a Ruby program that generates
Rust program that generates
Scala program that generates
...(through 128 languages in total)...
REXX program that generates
the original Ruby code again.

![Language Uroboros][langs]

[langs]: langs.png

(If you want to see the old 50-language version, see [50](https://github.com/mame/quine-relay/tree/50) branch.)

## Usage

### Ubuntu

If you are using Ubuntu 17.10 "Artful Aardvark", you can perform the following steps.

#### 1. Install all interpreters/compilers.

First, you have to type the following apt-get command to install all of them.

    $ sudo apt-get install afnix algol68g aplus-fsf aspectc++ aspectj \
      asymptote ats2-lang bash bc bf bison bsdgames bsh clisp clojure cmake \
      cmake coffeescript dafny dc ecere-dev elixir emacs25 erlang f2c fish \
      flex fp-compiler fsharp g++ gambas3-script gap gawk gcc gdb gdc genius \
      gforth gfortran ghc ghostscript gnat gnu-smalltalk gnuplot gobjc \
      golang gpt gri groff groovy guile-2.0 gzip haxe icont iconx intercal \
      iverilog jasmin-sable jq julia ksh libgd-dev libpng-dev lisaac \
      livescript llvm lua5.3 m4 make maxima minizinc mlton mono-devel \
      mono-mcs mono-vbnc nasm neko nescc nickle nim node-typescript nodejs \
      ocaml octave open-cobol openjdk-8-jdk pari-gp parser3-cgi perl php-cli \
      pike8.0 python r-base rakudo ratfor rc regina-rexx ruby ruby-mustache \
      rustc scala scilab sed slsh spin squirrel3 swi-prolog tcl tcsh valac \
      vim xsltproc yabasic yorick zoem zsh

Then, build the bundled interpreters.

    $ sudo apt-get install libpng-dev libgd-dev groff flex bison
    $ make -C vendor

#### 2. Run each program on each interpreter/compiler.

    $ ulimit -s unlimited
    $ ruby QR.rb > QR.rs
    $ rustc QR.rs && ./QR > QR.scala
    $ scalac QR.scala && scala QR > QR.scm
    $ guile QR.scm > QR.sci
    $ scilab -nwni -nb -f QR.sci > QR.sed
    $ sed -E -f QR.sed QR.sed > QR.spl
    $ ./vendor/local/bin/spl2c < QR.spl > QR.spl.c && gcc -o QR -I ./vendor/local/include -L ./vendor/local/lib QR.spl.c -lspl -lm &&
      ./QR > QR.sl
    $ slsh QR.sl > QR.st
    $ gst QR.st > QR.nut
    $ squirrel QR.nut > QR.sml
    $ mlton @MLton fixed-heap 200M -- QR.sml && ./QR > QR.sq
    $ ruby vendor/subleq.rb QR.sq > QR.tcl
    $ tclsh QR.tcl > QR.tcsh
    $ tcsh QR.tcsh > QR.t
    $ ruby vendor/thue.rb QR.t > QR.ts
    $ tsc --outFile QR.ts.js QR.ts && nodejs QR.ts.js > QR.unl
    $ ruby vendor/unlambda.rb QR.unl > QR.vala
    $ valac QR.vala && ./QR > QR.v
    $ iverilog -o QR QR.v && ./QR -vcd-none > QR.vim
    $ vim -EsS QR.vim > QR.vb
    $ vbnc QR.vb && mono ./QR.exe > QR.ws
    $ ruby vendor/whitespace.rb QR.ws > QR.xslt
    $ xsltproc QR.xslt > QR.yab
    $ yabasic QR.yab > QR.yorick
    $ yorick -batch QR.yorick > QR.azm
    $ zoem -i QR.azm > QR.zsh
    $ zsh QR.zsh > QR.+
    $ a+ QR.+ > qr.adb
    $ gnatmake qr.adb && ./qr > QR.als
    $ LD_LIBRARY_PATH=/usr/lib/afnix axi QR.als > QR.aheui
    $ go run vendor/goaheui/main.go QR.aheui > QR.a68
    $ a68g QR.a68 > QR.ante
    $ ruby vendor/ante.rb QR.ante > QR.cc
    $ ag++ -o QR QR.cc && ./QR > QR.aj
    $ ajc QR.aj && java QR > QR.asy
    $ asy QR.asy > QR.dats
    $ patscc -o QR QR.dats && ./QR > QR.awk
    $ awk -f QR.awk > QR.bash
    $ bash QR.bash > QR.bc
    $ BC_LINE_LENGTH=4000000 bc -q QR.bc > QR.bsh
    $ bsh QR.bsh > QR.bef
    $ cfunge QR.bef > QR.Blc
    $ ruby vendor/blc.rb < QR.Blc > QR.bf
    $ bf -c500000 QR.bf > QR.c
    $ gcc -o QR QR.c && ./QR > QR.cpp
    $ g++ -o QR QR.cpp && ./QR > QR.cs
    $ mcs QR.cs && mono QR.exe > QR.chef
    $ PERL5LIB=vendor/local/lib/perl5 compilechef QR.chef QR.chef.pl &&
      perl QR.chef.pl > QR.clj
    $ clojure QR.clj > QR.cmake
    $ cmake -P QR.cmake > QR.cob
    $ cobc -O2 -x QR.cob && ./QR > QR.coffee
    $ coffee --nodejs --stack_size=100000 QR.coffee > QR.lisp
    $ clisp QR.lisp > QR.d
    $ gdc -o QR QR.d && ./QR > QR.dfy
    $ dafny QR.dfy && mono QR.exe > QR.dc
    $ dc QR.dc > QR.ec
    $ ecp -c QR.ec -o QR.sym && ecc -c QR.ec -o QR.c && ecs -console QR.sym QR.imp -o QR.main.ec &&
      ecp -c QR.main.ec -o QR.main.sym && ecc -c QR.main.ec -o QR.main.c &&
      gcc -o QR QR.c QR.main.c -lecereCOM && ./QR > QR.exs
    $ elixir QR.exs > QR.el
    $ emacs -Q --script QR.el > QR.erl
    $ escript QR.erl > QR.fsx
    $ fsharpc QR.fsx -o QR.exe && mono QR.exe > QR.false
    $ ruby vendor/false.rb QR.false > QR.fl
    $ flex -o QR.fl.c QR.fl && gcc -o QR QR.fl.c && ./QR > QR.fish
    $ fish QR.fish > QR.fs
    $ gforth QR.fs > QR.f
    $ gfortran -o QR QR.f && ./QR > QR.f90
    $ gfortran -o QR QR.f90 && ./QR > QR.gbs
    $ gbs3 QR.gbs > QR.g
    $ gap -q QR.g > QR.gdb
    $ gdb -q -x QR.gdb > QR.gel
    $ genius QR.gel > QR.plt
    $ gnuplot QR.plt > QR.go
    $ go run QR.go > QR.gs
    $ ruby vendor/golfscript.rb QR.gs > QR.gpt
    $ gpt -o QR QR.gpt && ./QR > QR.grass
    $ ruby vendor/grass.rb QR.grass > QR.gri
    $ gri QR.gri > QR.groovy
    $ groovy QR.groovy > QR.gz
    $ gzip -cd QR.gz > QR.hs
    $ ghc QR.hs && ./QR > QR.hx
    $ haxe -main QR -neko QR.n && neko QR.n > QR.icn
    $ icont -s QR.icn && ./QR > QR.i
    $ ick -bfOc QR.i && gcc -static QR.c -I /usr/include/ick-* -o QR -lick &&
      ./QR > QR.j
    $ jasmin QR.j && java QR > QR.java
    $ javac QR.java && java QR > QR.js
    $ nodejs QR.js > QR.jq
    $ jq -r -n -f QR.jq > QR.jsfuck
    $ nodejs --stack_size=100000 QR.jsfuck > QR.jl
    $ julia QR.jl > QR.ksh
    $ ksh QR.ksh > QR.lazy
    $ lazyk QR.lazy > qr.li
    $ lisaac qr.li && ./qr > QR.ls
    $ lsc QR.ls > QR.ll
    $ llvm-as QR.ll && lli QR.bc > QR.lol
    $ lci QR.lol > QR.lua
    $ lua5.3 QR.lua > QR.m4
    $ m4 QR.m4 > QR.mk
    $ make -f QR.mk > QR.mac
    $ maxima -q --init-mac=QR.mac > QR.mzn
    $ mzn2fzn QR.mzn && fzn-gecode QR.fzn | solns2out --soln-sep '' QR.ozn > QR.il
    $ ilasm QR.il && mono QR.exe > QR.mustache
    $ mustache QR.mustache QR.mustache > QR.asm
    $ nasm -felf QR.asm && ld -m elf_i386 -o QR QR.o && ./QR > QR.neko
    $ nekoc QR.neko && neko QR.n > QR.nc
    $ nescc -o QR QR.nc && ./QR > QR.5c
    $ nickle QR.5c > QR.nim
    $ nim c QR.nim && ./QR > QR.m
    $ gcc -o QR QR.m && ./QR > QR.ml
    $ ocaml QR.ml > QR.octave
    $ mv QR.m QR.m.bak && octave -qf QR.octave > QR.ook && mv QR.m.bak QR.m
    $ ruby vendor/ook-to-bf.rb QR.ook QR.ook.bf && bf -c500000 QR.ook.bf > QR.gp
    $ gp -f -q QR.gp > QR.p
    $ parser3 QR.p > QR.pas
    $ fpc QR.pas && ./QR > QR.pl
    $ perl QR.pl > QR.pl6
    $ perl6 QR.pl6 > QR.php
    $ php QR.php > QR.png
    $ npiet QR.png > QR.pike
    $ pike QR.pike > QR.ps
    $ gs -dNODISPLAY -q QR.ps > QR.ppt
    $ ppt -d < QR.ppt > QR.prolog
    $ swipl -q -t qr -f QR.prolog > QR.pr
    $ spin -T QR.pr > QR.py
    $ python QR.py > QR.R
    $ R --slave -f QR.R > QR.ratfor
    $ ratfor -o QR.ratfor.f QR.ratfor && gfortran -o QR QR.ratfor.f &&
      ./QR > QR.rc
    $ rc QR.rc > QR.rexx
    $ rexx ./QR.rexx > QR2.rb

You will see that `QR.rb` is the same as `QR2.rb`.

    $ diff QR.rb QR2.rb

Alternatively, just type `make`.

    $ make

Note: It may require huge memory to compile some files.

### Arch Linux

Just install [quine-relay-git](https://aur.archlinux.org/packages/quine-relay-git/) from AUR and run `quine-relay`.
Report any problems as comments to the AUR package or to the respective packages, if one of the many compilers should have issues.

### Other platforms

You may find [instructions for other platforms in the wiki](https://github.com/mame/quine-relay/wiki/Installation).

If you are not using these Linux distributions, please find your way yourself.
If you could do it, please let me know.  Good luck.

## Tested interpreter/compiler versions

I used the following Ubuntu deb packages to test this program.

\#  |language           |ubuntu package  |version
----|-------------------|----------------|------------------------
1   |Ruby               |ruby            |1:2.3.3
2   |Rust               |rustc           |1.18.0+dfsg1-4ubuntu1
3   |Scala              |scala           |2.11.8-2
4   |Scheme             |guile-2.0       |2.0.13+1-4
5   |Scilab             |scilab          |5.5.2-4ubuntu2
6   |sed                |sed             |4.4-1
7   |Shakespeare        |*N/A*           |-
8   |S-Lang             |slsh            |2.3.1-5ubuntu1
9   |Smalltalk          |gnu-smalltalk   |3.2.5-1build3
10  |Squirrel           |squirrel3       |3.1-4
11  |Standard ML        |mlton           |20130715-3
12  |Subleq             |*N/A*           |-
13  |Tcl                |tcl             |8.6.0+9
14  |tcsh               |tcsh            |6.20.00-7
15  |Thue               |*N/A*           |-
16  |TypeScript         |node-typescript |2.5.2-1
17  |Unlambda           |*N/A*           |-
18  |Vala               |valac           |0.36.6-1
19  |Verilog            |iverilog        |10.1-0.1build1
20  |Vimscript          |vim             |2:8.0.0197-4ubuntu5
21  |Visual Basic       |mono-vbnc       |4.0.1-1
22  |Whitespace         |*N/A*           |-
23  |XSLT               |xsltproc        |1.1.29-2.1ubuntu1
24  |Yabasic            |yabasic         |1:2.78.2-2
25  |Yorick             |yorick          |2.2.04+dfsg1-6build1
26  |Zoem               |zoem            |11-166-1.2
27  |zsh                |zsh             |5.2-5ubuntu1
28  |A+                 |aplus-fsf       |4.22.1-9
29  |Ada                |gnat            |7ubuntu1
30  |AFNIX              |afnix           |2.8.0-3
31  |Aheui              |*N/A*           |-
32  |ALGOL 68           |algol68g        |2.8-2
33  |Ante               |*N/A*           |-
34  |AspectC++          |aspectc++       |1:2.2+git20170823-1
35  |AspectJ            |aspectj         |1.8.9-2
36  |Asymptote          |asymptote       |2.41-2build1
37  |ATS                |ats2-lang       |0.2.9-1
38  |Awk                |gawk            |1:4.1.4+dfsg-1
39  |bash               |bash            |4.4-5ubuntu1
40  |bc                 |bc              |1.06.95-9build2
41  |BeanShell          |bsh             |2.0b4-18
42  |Befunge            |*N/A*           |-
43  |BLC8               |*N/A*           |-
44  |Brainfuck          |bf              |20041219ubuntu5
45  |C                  |gcc             |4:7.2.0-1ubuntu1
46  |C++                |g++             |4:7.2.0-1ubuntu1
47  |C#                 |mono-mcs        |4.6.2.7+dfsg-1ubuntu1
48  |Chef               |*N/A*           |-
49  |Clojure            |clojure         |1.8.0-3
50  |CMake              |cmake           |3.9.1-1
51  |Cobol              |open-cobol      |1.1-2
52  |CoffeeScript       |coffeescript    |1.10.0~dfsg-1
53  |Common Lisp        |clisp           |1:2.49-10build1
54  |D                  |gdc             |4:7.2.0-1ubuntu1
55  |Dafny              |dafny           |1.9.7-1
56  |dc                 |dc              |1.06.95-9build2
57  |eC                 |ecere-dev       |0.44.15-1
58  |Elixir             |elixir          |1.3.3-2
59  |Emacs Lisp         |emacs25         |25.2+1-6
60  |Erlang             |erlang          |1:20.0.4+dfsg-1ubuntu1
61  |F#                 |fsharp          |4.0.0.4+dfsg2-2
62  |FALSE              |*N/A*           |-
63  |Flex               |flex            |2.6.1-1.3
64  |Fish               |fish            |2.6.0-1
65  |Forth              |gforth          |0.7.3+dfsg-4
66  |FORTRAN77          |f2c             |20100827-3
67  |Fortran90          |gfortran        |4:7.2.0-1ubuntu1
68  |Gambas script      |gambas3-script  |3.9.2-2build4
69  |GAP                |gap             |4r8p7-1
70  |GDB                |gdb             |8.0.1-0ubuntu1
71  |GEL (Genius)       |genius          |1.0.23-2
72  |Gnuplot            |gnuplot         |5.0.7+dfsg1-1
73  |Go                 |golang          |2:1.8~1ubuntu1
74  |GolfScript         |*N/A*           |-
75  |G-Portugol         |gpt             |1.1-4
76  |Grass              |*N/A*           |-
77  |Gri                |gri             |2.12.26-1
78  |Groovy             |groovy          |2.4.8-2
79  |Gzip               |gzip            |1.6-5ubuntu1
80  |Haskell            |ghc             |8.0.2-10
81  |Haxe               |haxe            |1:3.4.2-1ubuntu1
82  |Icon               |icont, iconx    |9.4.3-6ubuntu1
83  |INTERCAL           |intercal        |30:0.30-1
84  |Jasmin             |jasmin-sable    |2.5.0-1
85  |Java               |openjdk-8-jdk   |8u144-b01-2
86  |JavaScript         |nodejs          |6.11.4~dfsg-1ubuntu1
87  |Jq                 |jq              |1.5+dfsg-2
88  |JSFuck             |nodejs          |6.11.4~dfsg-1ubuntu1
89  |Julia              |julia           |0.4.7-7build2
90  |ksh                |ksh             |93u+20120801-3.1ubuntu1
91  |Lazy K             |*N/A*           |-
92  |Lisaac             |lisaac          |1:0.39~rc1-3
93  |LiveScript         |livescript      |1.5.0+dfsg-3build2
94  |LLVM asm           |llvm            |1:4.0-37~exp3ubuntu1
95  |LOLCODE            |*N/A*           |-
96  |Lua                |lua5.3          |5.3.3-1
97  |M4                 |m4              |1.4.18-1
98  |Makefile           |make            |4.1-9.1
99  |Maxima             |maxima          |5.40.0-1
100 |MiniZinc           |minizinc        |2.0.14+dfsg1-1
101 |MSIL               |mono-devel      |4.6.2.7+dfsg-1ubuntu1
102 |Mustache           |ruby-mustache   |1.0.2-1
103 |NASM               |nasm            |2.13.01-2
104 |Neko               |neko            |2.1.0-4
105 |nesC               |nescc           |1.3.5-1
106 |Nickle             |nickle          |2.79-2
107 |Nim                |nim             |0.17.2-1ubuntu1
108 |Objective-C        |gobjc           |4:7.2.0-1ubuntu1
109 |OCaml              |ocaml           |4.04.0-2ubuntu4
110 |Octave             |octave          |4.2.1-2build1
111 |Ook!               |*N/A*           |-
112 |PARI/GP            |pari-gp         |2.9.3-1
113 |Parser 3           |parser3-cgi     |3.4.5-2
114 |Pascal             |fp-compiler     |3.0.2+dfsg-5ubuntu1
115 |Perl 5             |perl            |5.26.0-8ubuntu1
116 |Perl 6             |rakudo          |2017.06-1
117 |PHP                |php-cli         |1:7.1+54ubuntu1
118 |Piet               |*N/A*           |-
119 |Pike               |pike8.0         |8.0.438-1
120 |PostScript         |ghostscript     |9.21~dfsg+1-0ubuntu3
121 |PPT (Punched tape) |bsdgames        |2.17-25
122 |Prolog             |swi-prolog      |7.4.2+dfsg-2
123 |Promela (Spin)     |spin            |6.4.6+dfsg-2
124 |Python             |python          |2.7.14-2ubuntu1
125 |R                  |r-base          |3.4.2-1ubuntu1
126 |Ratfor             |ratfor          |1.0-16
127 |rc                 |rc              |1.7.4-1
128 |REXX               |regina-rexx     |3.6-2.1

Note that some languages are not available in Ubuntu (marked as *N/A*).
This repository includes their implementations in `vendor/`.
See also `vendor/README` in detail.


## Frequently asked questions

### Q. Why?

A. [Take your pick](https://github.com/mame/quine-relay/issues/11).

### Q. How?

A. Good news: I published a book, ["The world of obfuscated, esoteric, artistic programming"](http://gihyo.jp/book/2015/978-4-7741-7643-7).
It explains how to write a quine, an ascii-art quine, and a uroboros quine like this quine-relay.
You can buy my book on [amazon.co.jp](http://www.amazon.co.jp/dp/4774176435).

(It also contains my almost all (about forty) works, including
[alphabet-only Ruby program](http://www.slideshare.net/mametter/ruby-esoteric-obfuscated-ruby-programming-5088683),
[radiation-hardened quine](https://github.com/mame/radiation-hardened-quine),
etc., and explains many techniques to write such programs.)

Bad news: It is written in Japanese.
I hope you could translate it to English <strike>and help me earn royalties</strike>.

### Q. Language XXX is missing!

A. See [the criteria for language inclusion][criteria] in detail.  (In short: please create a deb package and contribute it to Ubuntu.)

[criteria]: https://github.com/mame/quine-relay/wiki/Criteria-for-language-inclusion

### Q. Does it really work?

A. [![Build Status](https://travis-ci.org/mame/quine-relay.svg?branch=laboratory)](https://travis-ci.org/mame/quine-relay)

### Q. How long did it take you?

A. [Do you try to cross the world line?](https://github.com/mame/quine-relay/issues/60)

### Q. The code does not fit into my display!

A. [Here you go][thumbnail].

[thumbnail]: thumbnail.png

### Q. How was the code generated?

A.

    $ sudo apt-get install rake ruby-cairo ruby-rsvg2 ruby-gdk-pixbuf2 \
      optipng advancecomp ruby-chunky-png
    $ cd src
    $ rake2.0 clobber
    $ rake2.0

## License

The MIT License applies to all resources
*except* the files in the `vendor/` directory.

The files in the `vendor/` directory are from third-parties
and are distributed under different licenses.
See `vendor/README` in detail.

---

The MIT License (MIT)

Copyright (c) 2013, 2014, 2015, 2016, 2017 Yusuke Endoh (@mametter), @hirekoke

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
