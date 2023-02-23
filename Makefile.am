SUBDIRS		= elvi test examples

bin_SCRIPTS = surfraw surfraw-update-path
if OPENSEARCH
dist_bin_SCRIPTS = opensearch-discover opensearch-genquery
endif
devel_extra	= banner prebuild
if BASHCOMPLETIONS
noinst_DATA	= surfraw.bookmarks
else
noinst_DATA	= surfraw.bookmarks surfraw-bash-completion
endif
man_MANS = surfraw-update-path.1 surfraw.1 elvi.1sr
if OPENSEARCH
man_MANS += opensearch-discover.1 opensearch-genquery.1
endif

EXTRA_DIST	= surfraw.lsm.in surfraw.IN surfraw-update-path.IN\
          surfraw.spec.in aclocal.m4 HACKING STYLE \
		  surfraw.1.IN elvi.1sr.IN surfraw.bookmarks links.IN \
		  surfraw-bash-completion.IN surfraw.conf.IN \
		  $(devel_extra)

CLEANFILES = surfraw surfraw-update-path surfraw-update-path.1 surfraw.spec surfraw.lsm \
		surfraw.1 elvi.1sr links surfraw-bash-completion surfraw.conf surfraw.1 \
		elvi.1sr opensearch-discover.1 opensearch-genquery.1

BUILT_SOURCES = surfraw.conf

do_subst = sed -e 's|@ELVIDIR[@]|${ELVIDIR}|g'\
	    -e 's|@VERSION[@]|${VERSION}|g'\
	    -e 's|@PACKAGE_STRING[@]|${PACKAGE_STRING}|g'\
	    -e 's|@TEXTBROWSER[@]|${TEXTBROWSER}|g'\
	    -e 's|@GRAPHICALBROWSER[@]|${GRAPHICALBROWSER}|g'\
	    -e 's|@AWK[@]|${AWK}|g'\
	    -e 's|@PERL[@]|${PERL}|g'\
	    -e 's|@sysconfdir[@]|${sysconfdir}|g' \
	    -e 's|@prefix[@]|${prefix}|g' \
	    -e 's|@mandir[@]|${mandir}|g' \
	    $(srcdir)/$@.IN > $@.tmp

# These depend on the config variables, so they need rebuilding upon change
surfraw surfraw-update-path: Makefile
	-rm -f $@ $@.tmp
	$(do_subst)
	chmod +x $@.tmp
	mv $@.tmp $@
surfraw.conf surfraw-bash-completion elvi.1sr surfraw.1 links: Makefile
	-rm -f $@ $@.tmp
	$(do_subst)
	mv $@.tmp $@

# Now just list their dependencies
# Executables
surfraw: $(srcdir)/surfraw.IN
surfraw-update-path: $(srcdir)/surfraw-update-path.IN
# Data files
surfraw.conf: $(srcdir)/surfraw.conf.IN
surfraw-bash-completion: $(srcdir)/surfraw-bash-completion.IN
elvi.1sr: $(srcdir)/elvi.1sr.IN
surfraw.1: $(srcdir)/surfraw.1.IN
links: $(srcdir)/links.IN

surfraw-update-path.1: surfraw-update-path
	-rm -f $@
	pod2man $? > $@

 opensearch-discover.1: opensearch-discover
	-rm -f $@
	pod2man $? > $@

opensearch-genquery.1: opensearch-genquery
	-rm -f $@
	pod2man $? > $@

install-data-hook: links surfraw-bash-completion
	$(MKDIR_P) $(DESTDIR)@sysconfdir@/xdg/surfraw
	$(INSTALL_DATA) surfraw.conf $(DESTDIR)@sysconfdir@/xdg/surfraw/conf
	$(INSTALL_DATA) $(top_srcdir)/surfraw.bookmarks $(DESTDIR)@sysconfdir@/xdg/surfraw/bookmarks
	while read target link; \
	do \
		(cd $(DESTDIR)@mandir@/man1 && rm -f $$link && $(LN_S) $$target $$link); \
	done < links
if INSTALLSR
	(cd $(DESTDIR)@bindir@ && rm -f sr && $(LN_S) surfraw sr)
	(cd $(DESTDIR)@mandir@/man1 && rm -f sr.1 && $(LN_S) surfraw.1 sr.1)
endif
if BASHCOMPLETIONS
	$(MKDIR_P) $(DESTDIR)@datadir@/bash-completion/completions
	$(INSTALL_DATA) surfraw-bash-completion $(DESTDIR)@datadir@/bash-completion/completions/surfraw
if INSTALLSR
	(cd $(DESTDIR)@datadir@/bash-completion/completions && rm -f sr && $(LN_S) surfraw sr)
endif  # INSTALLSR
endif  # BASHCOMPLETIONS

uninstall-local: links
	rm -rf $(DESTDIR)@sysconfdir@/xdg/surfraw
	while read target link ;\
	do \
		rm -f $(DESTDIR)@mandir@/man1/$$link ;\
	done < links
if INSTALLSR
	rm -f $(DESTDIR)@bindir@/sr
	rm -f $(DESTDIR)@mandir@/man1/sr.1
endif
if BASHCOMPLETIONS
	-rm -f $(DESTDIR)@datadir@/bash-completion/completions/surfraw
if INSTALLSR
	-rm -f $(DESTDIR)@datadir@/bash-completion/completions/sr
endif  # INSTALLSR
endif  # BASHCOMPLETIONS


submit-lsm: surfraw.lsm
	mail -s add LSM@qqx.org < $?

test: all surfraw.conf
	make -C test test

.PHONY: test
