#generated by newprogram

#AM_CFLAGS=-Wall -Wextra -O2 -D_GNU_SOURCE=1
# Set up initially to use GDB, change to optimised afterward.
AM_CFLAGS=-Wall -Wextra -g -O0 -D_GNU_SOURCE=1

bin_PROGRAMS=newprogram

newprogram_SOURCES=newprogram.c dirs.c dirs.h files.c files.h str.c \
str.h firstrun.h firstrun.c gopt.h gopt.c

man_MANS=newprogram.1

# next lines to be hand edited
# send <whatever> to $(prefix)/share/
newdir=$(datadir)/newprogram
new_DATA=am.mak prdata.cfg goptC goptH mainC manpage.md
# ensure that newprogram.1 and any other config files get put in the
# tarball. Also stops `make distcheck` bringing an error.
EXTRA_DIST=newprogram.1 am.mak prdata.cfg goptC goptH mainC manpage.md
