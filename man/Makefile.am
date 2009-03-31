##
## Input file for automake
##
## Copyright (C) 2008, 2009 Francesco Salvestrini
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
		$(top_builddir)/yaxx-to-grammar
EXTRA_DIST += yacc-to-grammar.x

yapp-to-grammar.1: $(top_srcdir)/yaxx-to-grammar.in $(top_srcdir)/configure.ac
	$(HELP2MAN) \
		--include=$(srcdir)/yapp-to-grammar.x \
		--source="@PACKAGE_NAME@" \
		--manual="User Commands" \
		--section=1 \
		--output=$@ \
		$(top_builddir)/yaxx-to-grammar
EXTRA_DIST += yapp-to-grammar.x

bison-to-grammar.1: $(top_srcdir)/yaxx-to-grammar.in $(top_srcdir)/configure.ac
	$(HELP2MAN) \
		--include=$(srcdir)/bison-to-grammar.x \
		--source="@PACKAGE_NAME@" \
		--manual="User Commands" \
		--section=1 \
		--output=$@ \
		$(top_builddir)/yaxx-to-grammar
EXTRA_DIST += bison-to-grammar.x

yaxx-to-grammar.1: $(top_srcdir)/yaxx-to-grammar.in $(top_srcdir)/configure.ac
	$(HELP2MAN) \
		--include=$(srcdir)/yaxx-to-grammar.x \
		--source="@PACKAGE_NAME@" \
		--manual="User Commands" \
		--section=1 \
		--output=$@ \
		$(top_builddir)/yaxx-to-grammar
EXTRA_DIST += yaxx-to-grammar.x

##
## Maintainer related targets
##
update-local: Makefile

maintainer-check-local: Makefile
