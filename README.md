# newprogram
A C program to initiate a new C programming project.
## What it will do for you
1. It will create a new named project directory within your designated programs directory.
2. It will generate your _Makefile.am_ within your new project directory.
3. Optionally provide a list of software dependencies within the _Makefile.am_ and hardlink those software files into your project direcory if they reside within a named software source library or copy boilerplate files into the project directory if they reside in a named _Stubs_ directory.
4. Optionally name files for _extra distribution_ within the _Makefile.am._
5. Automatically provide the code in _Makefile.am_ to name the project manpage.

### Naming conventions
The names within the project are determined by the name you use when you run the program.  
For example
```
newprogram [option] SomeThing
```
1. Source directory will be: _Something_
2. The binary will be: _something_
3. Source code will be: _something.c_
4. And the manpage: _something.1_

No matter what case you use for the target name, the case of the resulting objects will be as shown above.

### The program generated it's own _Makefile.am_
#### Invocation
```
newprogram --depends 'dirs.c+h files.c+h str.c+h firstrun.c+h' -o -x 'paths.cfg am.mak' Newprogram
```
#### The _Makefile.am_ that was made
```
#generated by newprogram

#AM_CFLAGS=-Wall -Wextra -O2 -D_GNU_SOURCE=1
# Set up initially to use GDB, change to optimised afterward.
AM_CFLAGS=-Wall -Wextra -g -O0 -D_GNU_SOURCE=1

bin_PROGRAMS=newprogram

newprogram_SOURCES=newprogram.c dirs.c dirs.h files.c files.h str.c \
str.h firstrun.c firstrun.h gopt.h gopt.c

man_MANS=newprogram.1

# next lines to be hand edited
# send <whatever> to $(prefix)/share/
newdir=$(datadir)/newprogram
new_DATA=paths.cfg am.mak
# Ensure that newprogram.1 and any other config files get put in the
# tarball. Also stops `make distcheck` bringing an error.
EXTRA_DIST=newprogram.1 paths.cfg am.mak
```
This file is as generated by _newprogram_ except that I inserted the line break at _newprogram_SOURCES_.
## What you must do.
After you have built and installed the program you will need to have, or create a directory where program files reside. In addition to that you will need to have or make two directories under the _Programs_ directory. In my setup I have them as
_Srclib/Stubs_ and _Srclib/Components_. _Stubs_ is used for boilerplate code that is to be copied into the project dir. The _Components_ sub dir is to hold working library software in source code form.

On first run of _newprogram_ configuration files will be copied in to _$HOME/.config/newprogram/_ and you will be invited to edit those files so as to name your own directory structure.
### Your source code library and boilerplate source
The files _gopt.c_ and _gopt.h_ are candidates to copy into the boilerplate sub dir, because on re-using them they must be individually edited to fit the requirements of the program under construction. The other header and C files may or may not be useful for your needs. If they are they can be linked into the _Components_ sub dir along with whatever other library source software is in your possession.