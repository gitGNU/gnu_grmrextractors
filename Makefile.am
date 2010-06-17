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
## MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
## GNU General Public License for more details.
##
## You should have received a copy of the GNU General Public License along
## with this program; if not, write to the Free Software Foundation, Inc.,
## 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
##

include $(top_srcdir)/Makefile.sub

EXTRA_DIST =
BUILT_SOURCES =
CLEANFILES =
MAINTAINERCLEANFILES =

include $(top_srcdir)/Makefile.top

ACLOCAL_AMFLAGS = -I tools/autotools/m4 --install

SUBDIRS =					\
	tools					\
	.					\
	tests					\
	man					\
	site

##
## NOTE:
##     Options listed in AUTOMAKE_OPTIONS variable are applied on a
##     per-`Makefile' basis.
##
AUTOMAKE_OPTIONS = check-news

##
## NOTE:
##     Makefile.am included files are automatically distributed by automake
##     rules
##
EXTRA_DIST +=					\
	README COPYING INSTALL THANKS		\
	bootstrap .bootstrap			\
	perl.af

bin_SCRIPTS =					\
        yaxx-to-grammar

yaxx-to-grammar: Makefile yaxx-to-grammar.in
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

install-yapp-to-grammar: $(top_builddir)/yaxx-to-grammar
	rm -f $(DESTDIR)$(bindir)/yapp-to-grammar && \
	$(LN_S) $(DESTDIR)$(bindir)/yaxx-to-grammar \
	$(DESTDIR)$(bindir)/yapp-to-grammar || { \
		rm -f $(DESTDIR)$(bindir)/yapp-to-grammar ; \
		exit 1 ; \
	}

uninstall-yapp-to-grammar:
	rm -f $(DESTDIR)$(bindir)/yapp-to-grammar

install-yacc-to-grammar: $(top_builddir)/yaxx-to-grammar
	rm -f $(DESTDIR)$(bindir)/yacc-to-grammar && \
	$(LN_S) $(DESTDIR)$(bindir)/yaxx-to-grammar \
	$(DESTDIR)$(bindir)/yacc-to-grammar || { \
		rm -f $(DESTDIR)$(bindir)/yacc-to-grammar ; \
		exit 1 ; \
	}

uninstall-yacc-to-grammar:
	rm -f $(DESTDIR)$(bindir)/yacc-to-grammar

install-bison-to-grammar: $(top_builddir)/yaxx-to-grammar
	rm -f $(DESTDIR)$(bindir)/bison-to-grammar && \
	$(LN_S) $(DESTDIR)$(bindir)/yaxx-to-grammar \
	$(DESTDIR)$(bindir)/bison-to-grammar || { \
		rm -f $(DESTDIR)$(bindir)/bison-to-grammar ; \
		exit 1 ; \
	}

uninstall-bison-to-grammar:
	rm -f $(DESTDIR)$(bindir)/bison-to-grammar

install-exec-hook: install-yapp-to-grammar install-yacc-to-grammar install-bison-to-grammar

uninstall-hook: uninstall-yapp-to-grammar uninstall-yacc-to-grammar uninstall-bison-to-grammar

##
## Maintainer related targets
##

site: all
	(cd site && $(MAKE) $(AM_MAKEFLAGS) site)

URL_BU = "http://github.com/salvestrini/build-utils/raw/master/maint"

EXTERNAL =                                      \
        $(URL_BU)/bootstrap

update-local: Makefile
	rm -r -f fetch-dir && \
	mkdir fetch-dir && \
	for i in $(EXTERNAL) ; do \
	        URL="$$i" ; \
	        NAME=`echo "$$i" | $(SED) -e 's,^.*/,,'` ; \
	        $(FETCH) $$URL?raw=true fetch-dir/$$NAME && \
	        mv fetch-dir/$$NAME $$NAME || { \
	                rm -f fetch-dir/$$NAME ; \
	                exit 1 ; \
	        } \
	done && \
	rm -r -f fetch-dir
	chmod a+x bootstrap || { exit 1 ; }

maintainer-check-parameters: Makefile $(bin_SCRIPTS)
	for i in $(bin_SCRIPTS) ; do \
		echo @ECHO_N@ "Checking standard parameters for $$i... " ; \
		if ( ./$$i -h 2>&1 > /dev/null ) ; then \
			echo "@ECHO_T@ok" ; \
		else \
			echo "@ECHO_T@error" ; \
			exit 1 ; \
		fi ; \
	done

maintainer-check-whitespaces: Makefile $(bin_SCRIPTS)
	$(WHITESPACE_DETECT) $(bin_SCRIPTS)

maintainer-check-wordwraps: Makefile $(bin_SCRIPTS)
	$(WORDWRAP_DETECT) -tab-size 8 --columns 80 $(bin_SCRIPTS)

maintainer-check-local: Makefile		\
	maintainer-check-whitespaces		\
	maintainer-check-wordwraps		\
	maintainer-check-parameters
