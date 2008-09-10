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

ACLOCAL_AMFLAGS = -I tools/autotools/m4

SUBDIRS =					\
	tools

EXTRA_DIST =
CLEANFILES =

bin_SCRIPTS =					\
        yaxx-to-grammar

yaxx-to-grammar$(EXEEXT): Makefile yaxx-to-grammar.in
	( rm -f $@ $@.tmp && \
	  $(do_subst) < $(srcdir)/yaxx-to-grammar.in > $@.tmp && \
	  chmod +x $@.tmp && \
	  chmod a-w $@.tmp && \
	  mv -f $@.tmp $@ ) || { \
		rm -f $@ $@.tmp ; \
		exit 1 ; \
	}
CLEANFILES += yaxx-to-grammar
EXTRA_DIST += yaxx-to-grammar.in

dist_man_MANS =					\
	yacc-to-grammar.1			\
	yapp-to-grammar.1			\
	yaxx-to-grammar.1

yacc-to-grammar.1: $(top_srcdir)/yaxx-to-grammar.in configure.ac
	$(HELP2MAN) \
		--include=$(srcdir)/yacc-to-grammar.x \
		--source="FSF" \
		--manual="User Commands" \
		--section=1 \
		--output=$@ \
		$(top_builddir)/yaxx-to-grammar
EXTRA_DIST += yacc-to-grammar.x

yapp-to-grammar.1: $(top_srcdir)/yaxx-to-grammar.in configure.ac
	$(HELP2MAN) \
		--include=$(srcdir)/yapp-to-grammar.x \
		--source="FSF" \
		--manual="User Commands" \
		--section=1 \
		--output=$@ \
		$(top_builddir)/yaxx-to-grammar
EXTRA_DIST += yapp-to-grammar.x

yaxx-to-grammar.1: $(top_srcdir)/yaxx-to-grammar.in configure.ac
	$(HELP2MAN) \
		--include=$(srcdir)/yaxx-to-grammar.x \
		--source="FSF" \
		--manual="User Commands" \
		--section=1 \
		--output=$@ \
		$(top_builddir)/yaxx-to-grammar
EXTRA_DIST += yaxx-to-grammar.x

install-yapp-to-grammar: yaxx-to-grammar
	rm -f $(DESTDIR)$(bindir)/yapp-to-grammar$(EXEEXT) && \
	$(LN_S) $(DESTDIR)$(bindir)/yaxx-to-grammar$(EXEEXT) \
	$(DESTDIR)$(bindir)/yapp-to-grammar$(EXEEXT) || { \
		rm -f $(DESTDIR)$(bindir)/yapp-to-grammar$(EXEEXT) ; \
		exit 1 ; \
	}

uninstall-yapp-to-grammar:
	rm -f $(DESTDIR)$(bindir)/yapp-to-grammar$(EXEEXT)

install-yacc-to-grammar: yaxx-to-grammar
	rm -f $(DESTDIR)$(bindir)/yacc-to-grammar$(EXEEXT) && \
	$(LN_S) $(DESTDIR)$(bindir)/yaxx-to-grammar$(EXEEXT) \
	$(DESTDIR)$(bindir)/yacc-to-grammar$(EXEEXT) || { \
		rm -f $(DESTDIR)$(bindir)/yacc-to-grammar$(EXEEXT) ; \
		exit 1 ; \
	}

uninstall-yacc-to-grammar:
	rm -f $(DESTDIR)$(bindir)/yacc-to-grammar$(EXEEXT)

install-exec-hook: install-yapp-to-grammar install-yacc-to-grammar

uninstall-hook:  uninstall-yapp-to-grammar uninstall-yacc-to-grammar

#
# NOTE:
#     Options listed in AUTOMAKE_OPTIONS variable are applied on a
#     per-`Makefile' basis.
#
AUTOMAKE_OPTIONS = check-news

##
## NOTE:
##     Makefile.sub is automatically distributed by automake rules
##
EXTRA_DIST +=							\
	BUGS TODO README NEWS COPYING AUTHORS INSTALL THANKS	\
	bootstrap						\
	configure.ac.in						\
	perl.af

dist-hook:
	$(GITLOG_TO_CHANGELOG) > $(distdir)/ChangeLog || {	\
		rm -f ChangeLog ;				\
		exit 1 ;					\
	}

##
## Maintainer related targets
##

HOST = "http://git.savannah.gnu.org/gitweb/?p=gnulib.git;a=blob_plain;hb=HEAD;f="

update-download:
	rm -r -f fetch-dir && \
	mkdir fetch-dir && \
	$(FETCH) $(HOST)doc/INSTALL fetch-dir/INSTALL && \
	chmod a+r fetch-dir/INSTALL && \
	chmod u+w fetch-dir/INSTALL && \
	$(FETCH) $(HOST)doc/COPYINGv2 fetch-dir/COPYING && \
	chmod a+r fetch-dir/COPYING && \
	chmod u+w fetch-dir/COPYING && \
	mv -f fetch-dir/* ./ || { \
		rm -r -f fetch-dir ; \
		exit 1 ; \
	} && \
	rm -r -f fetch-dir

update-local: Makefile update-download 

maintainer-check-parameters: Makefile $(scripts)
	for i in $(scripts) ; do \
		echo @ECHO_N@ "Checking standard parameters for $$i... " ; \
		if ( ./$$i -h 2>&1 > /dev/null ) ; then \
			echo "@ECHO_T@ok" ; \
		else \
			echo "@ECHO_T@error" ; \
			exit 1 ; \
		fi ; \
	done

maintainer-check-local: Makefile maintainer-check-parameters
