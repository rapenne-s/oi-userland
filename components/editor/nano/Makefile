#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL)". You may
# only use this file in accordance with the terms of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source. A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright (c) 2014 Rouven Wachhaus
# Copyright (c) 2019 Michal Nowak
#

BUILD_BITS=		64

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		nano
COMPONENT_VERSION=	4.5
COMPONENT_FMRI=		editor/nano
COMPONENT_SUMMARY=	GNU implementation of nano, a text editor emulating pico
COMPONENT_CLASSIFICATION=System/Text Tools
COMPONENT_PROJECT_URL=	https://www.nano-editor.org/
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.xz
COMPONENT_ARCHIVE_HASH=	\
	sha256:ded5c38f5ecd9de2b624e0db8013a375c169d3fbbd49575967b868847df8f533
COMPONENT_ARCHIVE_URL=	http://ftp.gnu.org/pub/gnu/nano/$(COMPONENT_ARCHIVE)
COMPONENT_LICENSE=	GPLv3

TEST_TARGET=		$(NO_TESTS)

include $(WS_MAKE_RULES)/common.mk

CONFIGURE_BINDIR.64 =	$(CONFIGURE_PREFIX)/bin

CONFIGURE_OPTIONS +=	--sysconfdir=/etc
CONFIGURE_OPTIONS +=	--enable-color
CONFIGURE_OPTIONS +=	--enable-multibuffer
CONFIGURE_OPTIONS +=	--enable-utf8
# magic does not identify files given their content
CONFIGURE_OPTIONS +=	--disable-libmagic
CONFIGURE_OPTIONS +=	get_wch=getwch

CPPFLAGS += -I$(USRINCDIR)/ncurses
CFLAGS += -I$(USRINCDIR)/ncurses

COMPONENT_POST_INSTALL_ACTION = \
	$(INSTALL) -D -m 0644 $(BUILD_DIR)/$(MACH64)/doc/sample.nanorc $(PROTO_DIR)$(ETCDIR)/nanorc

# Auto-generated dependencies
REQUIRED_PACKAGES += library/ncurses
REQUIRED_PACKAGES += system/library
