
@SET_MAKE@

EXTRA_DIST=BUGS FAQ TRANSLATORS README.hooks html lang images contrib

htmllibdir=@htmllibdir@
htmldir=@htmldir@
imagedir=@imagedir@
QA_PACKAGE=@QA_PACKAGE@
QA_VERSION=@QA_VERSION@
PACKAGE=@QA_PACKAGE@
VERSION=@QA_VERSION@

#
# Install qmailadmin setuid to @vpopuser@
#
INSTALL_PROGRAM=${INSTALL} -o @vpopuser@ -m 6755 -g @vpopgroup@ $(AM_INSTALL_PROGRAM_FLAGS)
INSTALL_STRIP_PROGRAM=${INSTALL_PROGRAM} -s

bindir=@cgibindir@
bin_PROGRAMS=@CGIBINTARGETS@
EXTRA_PROGRAMS=qmailadmin

qmailadmin_DEPENDENCIES=$(COMMONDEPENDENCIES)

COMMONSOURCES=qmailadmin.c alias.c autorespond.c forward.c mailinglist.c \
	      user.c util.c printh.c auth.c template.c \
	      command.c show.c cgi.c limits.c dotqmail.c \
	      qmailadmin.h qmailadminx.h

qmailadmin_SOURCES=$(COMMONSOURCES) 
qmailadmin_LDADD=@auth_libs@

qmailadmin.o: config.h qmailadmin.h 
alias.o: config.h qmailadmin.h qmailadminx.h 
autorespond.o: config.h qmailadmin.h qmailadminx.h 
forward.o: config.h qmailadmin.h qmailadminx.h 
mailinglist.o: config.h qmailadmin.h qmailadminx.h 
user.o: config.h qmailadmin.h qmailadminx.h 
util.o: config.h qmailadmin.h qmailadminx.h 
printh.o: printh.h
auth.o: config.h qmailadmin.h qmailadminx.h 
template.o: config.h qmailadmin.h qmailadminx.h 
command.o: qmailadmin.h qmailadminx.h 
show.o: config.h qmailadmin.h qmailadminx.h 
cgi.o: config.h qmailadmin.h qmailadminx.h 
limits.o: config.h qmailadmin.h qmailadminx.h 
dotqmail.o: config.h qmailadmin.h qmailadminx.h 

DEFS=-I. @auth_incs@ 

# Maintainer stuff

dist-rpm:
	cp @QA_PACKAGE@-@QA_VERSION@.tar.gz $$HOME/src/rpm/SOURCES
	cp @QA_PACKAGE@.spec $$HOME/src/rpm/SPECS
	cd $$HOME/src/rpm/SPECS && rpm -ba --sign @QA_PACKAGE@.spec
	rm -rf htmldist
	mkdir htmldist
	ln NEWS.html htmldist/index.html
	ln $$HOME/src/rpm/SRPMS/@QA_PACKAGE@-@QA_VERSION@-1.src.rpm @QA_PACKAGE@-@QA_VERSION@.tar.gz htmldist

dist-hook:

# use the [^C]* pattern to skip the CVS directory
install-data-local:
	$(mkinstalldirs)         $(DESTDIR)@htmllibdir@
	rm -rf                   $(DESTDIR)@htmllibdir@/html
	$(mkinstalldirs)         $(DESTDIR)@htmllibdir@/html 
	cp $(srcdir)/html/*.html $(DESTDIR)@htmllibdir@/html
	cp $(srcdir)/html/colortable $(DESTDIR)@htmllibdir@/html
	chmod 755                $(DESTDIR)@htmllibdir@/html
	chmod 644                $(DESTDIR)@htmllibdir@/html/*
	rm -rf                   $(DESTDIR)@htmllibdir@/lang
	$(mkinstalldirs)         $(DESTDIR)@htmllibdir@/lang 
	cp $(srcdir)/lang/??     $(DESTDIR)@htmllibdir@/lang
	cp $(srcdir)/lang/??-??  $(DESTDIR)@htmllibdir@/lang
	chmod 755                $(DESTDIR)@htmllibdir@/lang
	chmod 644                $(DESTDIR)@htmllibdir@/lang/*
	$(mkinstalldirs)         $(DESTDIR)@imagedir@
	cp $(srcdir)/images/*.png $(DESTDIR)@imagedir@
	cp $(srcdir)/images/*.css $(DESTDIR)@imagedir@
