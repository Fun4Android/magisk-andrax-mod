# Installation directories.
PREFIX ?= /usr
SBINDIR ?= $(PREFIX)/sbin
MANDIR = $(PREFIX)/share/man
BASHCOMPLETIONDIR ?= $(PREFIX)/share/bash-completion/completions

CFLAGS ?= -Werror -Wall -W
override LDLIBS += -lsepol -lselinux -lsemanage
SETSEBOOL_OBJS = setsebool.o

BASHCOMPLETIONS=setsebool-bash-completion.sh 

all: setsebool

setsebool: $(SETSEBOOL_OBJS)

install: all
	-mkdir -p $(DESTDIR)$(SBINDIR)
	install -m 755 setsebool $(DESTDIR)$(SBINDIR)
	-mkdir -p $(DESTDIR)$(MANDIR)/man8
	install -m 644 setsebool.8 $(DESTDIR)$(MANDIR)/man8/
	-mkdir -p $(DESTDIR)$(BASHCOMPLETIONDIR)
	install -m 644 $(BASHCOMPLETIONS) $(DESTDIR)$(BASHCOMPLETIONDIR)/setsebool

relabel:

clean:
	-rm -f setsebool *.o

indent:
	../../scripts/Lindent $(wildcard *.[ch])

