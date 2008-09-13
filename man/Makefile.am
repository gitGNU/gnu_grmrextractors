##
## Input file for automake
##
## Copyright (C) 2007, 2008 Francesco Salvestrini
##
## This program is free software; you can redistribute it and/or modify
## it under the terms of the GNU General Public License as published by
## the Free Software Foundation; either version 2 of the License, or
## (at your option) any later version.
##
## This program is distributed in the hope that it will be useful,
## but WITHOUT ANY WARRANTY; without even the implied warranty of
## MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.	 See the
## GNU General Public License for more details.
##
## You should have received a copy of the GNU General Public License along
## with this program; if not, write to the Free Software Foundation, Inc.,
## 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
##

include $(top_srcdir)/Makefile.sub

EXTRA_DIST =
CLEANFILES =

dist_man_MANS =					\
	bison-to-grammar.1			\
	yacc-to-grammar.1			\
	yapp-to-grammar.1			\
	yaxx-to-grammar.1

yacc-to-grammar.1: $(top_srcdir)/yaxx-to-grammar.in $(top_srcdir)/configure.ac
	$(HELP2MAN) \
		--include=$(srcdir)/yacc-to-grammar.x \
		--source="@PACKAGE_NAME@" \
		--manual="User Commands" \
		--section=1 \
		--output=$@ \
		$(top_builddir)/yaxx-to-grammar$(EXEEXT)
EXTRA_DIST += yacc-to-grammar.x

yapp-to-grammar.1: $(top_srcdir)/yaxx-to-grammar.in $(top_srcdir)/configure.ac
	$(HELP2MAN) \
		--include=$(srcdir)/yapp-to-grammar.x \
		--source="@PACKAGE_NAME@" \
		--manual="User Commands" \
		--section=1 \
		--output=$@ \
		$(top_builddir)/yaxx-to-grammar$(EXEEXT)
EXTRA_DIST += yapp-to-grammar.x

bison-to-grammar.1: $(top_srcdir)/yaxx-to-grammar.in $(top_srcdir)/configure.ac
	$(HELP2MAN) \
		--include=$(srcdir)/bison-to-grammar.x \
		--source="@PACKAGE_NAME@" \
		--manual="User Commands" \
		--section=1 \
		--output=$@ \
		$(top_builddir)/yaxx-to-grammar$(EXEEXT)
EXTRA_DIST += bison-to-grammar.x

yaxx-to-grammar.1: $(top_srcdir)/yaxx-to-grammar.in $(top_srcdir)/configure.ac
	$(HELP2MAN) \
		--include=$(srcdir)/yaxx-to-grammar.x \
		--source="@PACKAGE_NAME@" \
		--manual="User Commands" \
		--section=1 \
		--output=$@ \
		$(top_builddir)/yaxx-to-grammar$(EXEEXT)
EXTRA_DIST += yaxx-to-grammar.x

install-yapp-to-grammar: $(top_builddir)/yaxx-to-grammar$(EXEEXT)
	rm -f $(DESTDIR)$(bindir)/yapp-to-grammar$(EXEEXT) && \
	$(LN_S) $(DESTDIR)$(bindir)/yaxx-to-grammar$(EXEEXT) \
	$(DESTDIR)$(bindir)/yapp-to-grammar$(EXEEXT) || { \
		rm -f $(DESTDIR)$(bindir)/yapp-to-grammar$(EXEEXT) ; \
		exit 1 ; \
	}

uninstall-yapp-to-grammar:
	rm -f $(DESTDIR)$(bindir)/yapp-to-grammar$(EXEEXT)

install-yacc-to-grammar: $(top_builddir)/yaxx-to-grammar$(EXEEXT)
	rm -f $(DESTDIR)$(bindir)/yacc-to-grammar$(EXEEXT) && \
	$(LN_S) $(DESTDIR)$(bindir)/yaxx-to-grammar$(EXEEXT) \
	$(DESTDIR)$(bindir)/yacc-to-grammar$(EXEEXT) || { \
		rm -f $(DESTDIR)$(bindir)/yacc-to-grammar$(EXEEXT) ; \
		exit 1 ; \
	}

uninstall-yacc-to-grammar:
	rm -f $(DESTDIR)$(bindir)/yacc-to-grammar$(EXEEXT)

install-bison-to-grammar: $(top_builddir)/yaxx-to-grammar$(EXEEXT)
	rm -f $(DESTDIR)$(bindir)/bison-to-grammar$(EXEEXT) && \
	$(LN_S) $(DESTDIR)$(bindir)/yaxx-to-grammar$(EXEEXT) \
	$(DESTDIR)$(bindir)/bison-to-grammar$(EXEEXT) || { \
		rm -f $(DESTDIR)$(bindir)/bison-to-grammar$(EXEEXT) ; \
		exit 1 ; \
	}

uninstall-bison-to-grammar:
	rm -f $(DESTDIR)$(bindir)/bison-to-grammar$(EXEEXT)

install-exec-hook: install-yapp-to-grammar install-yacc-to-grammar install-bison-to-grammar

uninstall-hook:  uninstall-yapp-to-grammar uninstall-yacc-to-grammar uninstall-bison-to-grammar

##
## Maintainer related targets
##
update-local: Makefile

maintainer-check-local: Makefile
