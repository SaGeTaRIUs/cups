#
# "$Id: Makefile 10191 2012-01-20 19:00:32Z mike $"
#
#   Port monitor makefile for CUPS.
#
#   Copyright 2007-2012 by Apple Inc.
#   Copyright 2006 by Easy Software Products.
#
#   These coded instructions, statements, and computer programs are the
#   property of Apple Inc. and are protected by Federal copyright
#   law.  Distribution and use rights are outlined in the file "LICENSE.txt"
#   which should have been included with this file.  If this file is
#   file is missing or damaged, see the license at "http://www.cups.org/".
#
#   This file is subject to the Apple OS-Developed Software exception.
#

include ../Makedefs

TARGETS	=	bcp tbcp

OBJS	=	bcp.o tbcp.o


#
# Make all targets...
#

all:	$(TARGETS)


#
# Make library targets...
#

libs:


#
# Make unit tests...
#

unittests:


#
# Clean all object files...
#

clean:
	$(RM) $(OBJS) $(TARGETS)


#
# Update dependencies (without system header dependencies...)
#

depend:
	$(CC) -MM $(ALL_CFLAGS) $(OBJS:.o=.c) >Dependencies


#
# Install all targets...
#

install:	all install-data install-headers install-libs install-exec


#
# Install data files...
#

install-data:


#
# Install programs...
#

install-exec:
	$(INSTALL_DIR) -m 755 $(SERVERBIN)/monitor
	for file in $(TARGETS); do \
		$(INSTALL_BIN) $$file $(SERVERBIN)/monitor; \
	done
	if test "x$(SYMROOT)" != "x"; then \
		$(INSTALL_DIR) $(SYMROOT); \
		for file in $(TARGETS); do \
			cp $$file $(SYMROOT); \
		done \
	fi


#
# Install headers...
#

install-headers:


#
# Install libraries...
#

install-libs:


#
# Uninstall all targets...
#

uninstall:
	for file in $(TARGETS); do \
		$(RM) $(SERVERBIN)/monitor/$$file; \
	done
	-$(RMDIR) $(SERVERBIN)/monitor
	-$(RMDIR) $(SERVERBIN)


#
# bcp
#

bcp:	bcp.o ../cups/$(LIBCUPS)
	echo Linking $@...
	$(CC) $(LDFLAGS) -o $@ bcp.o $(LIBS)


#
# tbcp
#

tbcp:	tbcp.o ../cups/$(LIBCUPS)
	echo Linking $@...
	$(CC) $(LDFLAGS) -o $@ tbcp.o $(LIBS)


#
# Dependencies...
#

include Dependencies


#
# End of "$Id: Makefile 10191 2012-01-20 19:00:32Z mike $".
#
