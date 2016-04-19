Oniguruma
=========

https://github.com/kkos/oniguruma

Oniguruma is a regular expressions library.
The characteristics of this library is that different character encoding
for every regular expression object can be specified.

Supported character encodings:

  ASCII, UTF-8, UTF-16BE, UTF-16LE, UTF-32BE, UTF-32LE,
  EUC-JP, EUC-TW, EUC-KR, EUC-CN,
  Shift_JIS, Big5, GB18030, KOI8-R, CP1251,
  ISO-8859-1, ISO-8859-2, ISO-8859-3, ISO-8859-4, ISO-8859-5,
  ISO-8859-6, ISO-8859-7, ISO-8859-8, ISO-8859-9, ISO-8859-10,
  ISO-8859-11, ISO-8859-13, ISO-8859-14, ISO-8859-15, ISO-8859-16

* GB18030: contributed by KUBO Takehiro
* CP1251:  contributed by Byte


License
-------

  BSD license.


Install
-------

### Case 1: Unix and Cygwin platform

   1. autoreconf -vfi   (* case: configure script is not found.)

   2. ./configure
   3. make
   4. make install

   * uninstall

     make uninstall

   * configuration check

     onig-config --cflags
     onig-config --libs
     onig-config --prefix
     onig-config --exec-prefix



### Case 2: Windows 64/32bit platform (Visual Studio)

   execute make_win64 or make_win32

      onig_s.lib:  static link library
      onig.dll:    dynamic link library

   * test (ASCII/Shift_JIS)

      1. cd src
      2. copy ..\windows\testc.c .
      3. nmake -f Makefile.windows ctest

   (I have checked by Visual Studio Community 2015)



Regular Expressions
-------------------

  See [doc/RE](doc/RE) or [doc/RE.ja](doc/RE.ja) for Japanese.


Usage
-----

  Include oniguruma.h in your program. (Oniguruma API)
  See doc/API for Oniguruma API.

  If you want to disable UChar type (== unsigned char) definition
  in oniguruma.h, define ONIG_ESCAPE_UCHAR_COLLISION and then 
  include oniguruma.h.

  If you want to disable regex_t type definition in oniguruma.h,
  define ONIG_ESCAPE_REGEX_T_COLLISION and then include oniguruma.h.

  Example of the compiling/linking command line in Unix or Cygwin,
  (prefix == /usr/local case)

    cc sample.c -L/usr/local/lib -lonig


  If you want to use static link library(onig_s.lib) in Win32,
  add option -DONIG_EXTERN=extern to C compiler.



Sample Programs
---------------

|File               |Description                              |
|:------------------|:----------------------------------------|
|sample/simple.c    |example of the minimum (Oniguruma API)   |
|sample/names.c     |example of the named group callback.     |
|sample/encode.c    |example of some encodings.               |
|sample/listcap.c   |example of the capture history.          |
|sample/posix.c     |POSIX API sample.                        |
|sample/sql.c       |example of the variable meta characters. |


Test Programs

|File               |Description                            |
|:------------------|:--------------------------------------|
|sample/syntax.c    |Perl, Java and ASIS syntax test.       |
|sample/crnl.c      |--enable-crnl-as-line-terminator test  |



Source Files
------------

|File               |Description                                             |
|:------------------|:-------------------------------------------------------|
|oniguruma.h        |Oniguruma API header file (public)                      |
|onig-config.in     |configuration check program template                    |
|regenc.h           |character encodings framework header file               |
|regint.h           |internal definitions                                    |
|regparse.h         |internal definitions for regparse.c and regcomp.c       |
|regcomp.c          |compiling and optimization functions                    |
|regenc.c           |character encodings framework                           |
|regerror.c         |error message function                                  |
|regext.c           |extended API functions (deluxe version API)             |
|regexec.c          |search and match functions                              |
|regparse.c         |parsing functions.                                      |
|regsyntax.c        |pattern syntax functions and built-in syntax definitions|
|regtrav.c          |capture history tree data traverse functions            |
|regversion.c       |version info function                                   |
|st.h               |hash table functions header file                        |
|st.c               |hash table functions                                    |
|oniggnu.h          |GNU regex API header file (public)                      |
|reggnu.c           |GNU regex API functions                                 |
|onigposix.h        |POSIX API header file (public)                          |
|regposerr.c        |POSIX error message function                            |
|regposix.c         |POSIX API functions                                     |
|mktable.c          |character type table generator                          |
|ascii.c            |ASCII encoding                                          |
|euc_jp.c           |EUC-JP encoding                                         |
|euc_tw.c           |EUC-TW encoding                                         |
|euc_kr.c           |EUC-KR, EUC-CN encoding                                 |
|sjis.c             |Shift_JIS encoding                                      |
|big5.c             |Big5      encoding                                      |
|gb18030.c          |GB18030   encoding                                      |
|koi8.c             |KOI8      encoding                                      |
|koi8_r.c           |KOI8-R    encoding                                      |
|cp1251.c           |CP1251    encoding                                      |
|iso8859_1.c        |ISO-8859-1 (Latin-1)                                    |
|iso8859_2.c        |ISO-8859-2 (Latin-2)                                    |
|iso8859_3.c        |ISO-8859-3 (Latin-3)                                    |
|iso8859_4.c        |ISO-8859-4 (Latin-4)                                    |
|iso8859_5.c        |ISO-8859-5 (Cyrillic)                                   |
|iso8859_6.c        |ISO-8859-6 (Arabic)                                     |
|iso8859_7.c        |ISO-8859-7 (Greek)                                      |
|iso8859_8.c        |ISO-8859-8 (Hebrew)                                     |
|iso8859_9.c        |ISO-8859-9 (Latin-5 or Turkish)                         |
|iso8859_10.c       |ISO-8859-10 (Latin-6 or Nordic)                         |
|iso8859_11.c       |ISO-8859-11 (Thai)                                      |
|iso8859_13.c       |ISO-8859-13 (Latin-7 or Baltic Rim)                     |
|iso8859_14.c       |ISO-8859-14 (Latin-8 or Celtic)                         |
|iso8859_15.c       |ISO-8859-15 (Latin-9 or West European with Euro)        |
|iso8859_16.c       |ISO-8859-16 (Latin-10)                                  |
|utf8.c             |UTF-8    encoding                                       |
|utf16_be.c         |UTF-16BE encoding                                       |
|utf16_le.c         |UTF-16LE encoding                                       |
|utf32_be.c         |UTF-32BE encoding                                       |
|utf32_le.c         |UTF-32LE encoding                                       |
|unicode.c          |Unicode information data                                |
|win32/Makefile     |Makefile for Win32 (VC++)                               |
|win32/config.h     |config.h for Win32                                      |
