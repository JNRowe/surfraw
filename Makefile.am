# $Id$
SUBDIRS		= elvi debian

bin_SCRIPTS	= surfraw surfraw-update-path W
sysconf_DATA	= surfraw.conf
devel_extra	= banner prebuild
man_MANS = surfraw-update-path.1
EXTRA_DIST	= surfraw.lsm.in surfraw.IN surfraw-update-path.IN\
                  surfraw.spec.in aclocal.m4 HACKING Makefile.include \
		  $(devel_extra)
CLEANFILES = surfraw surfraw-update-path surfraw-update-path.1 surfraw.spec surfraw.lsm

surfraw: surfraw.IN

surfraw-update-path: surfraw-update-path.IN

surfraw-update-path.1: surfraw-update-path
	-rm -f $@
	pod2man $< > $@


include $(top_srcdir)/Makefile.include

#htdocs: index.html
#	scp index.html surfraw.sourceforge.net:/home/groups/s/su/surfraw/htdocs/index.html
#README: index.html
#	st=`stty -g`; stty cols 80; lynx -dump $< >$@ || rm -f $@; stty $$st
#ftp:
#	scp $(PACKAGE)-$(VERSION).tar.gz proff@ftp.netbsd.org:/pub/NetBSD/misc/proff/
#download:
#	ncftpput -F download.sourceforge.net /incoming $(PACKAGE)-$(VERSION).tar.gz
