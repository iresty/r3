SUBDIRS=src . examples

if ENABLE_CHECK
SUBDIRS += tests
endif

lib_LTLIBRARIES = libr3.la
libr3_la_SOURCES =
libr3_la_LIBADD = src/libr3core.la
libr3_la_LDFLAGS =

AM_CFLAGS= $(DEPS_CFLAGS) $(R3_CC_OPT) $(GVC_DEPS_CFLAGS) -I$(top_builddir) -I$(top_builddir)/include -Wall -std=c99
AM_LDFLAGS=$(DEPS_LIBS) $(R3_LD_OPT) $(GVC_DEPS_LIBS)

ACLOCAL_AMFLAGS=-I m4

if ENABLE_DEBUG
AM_CFLAGS += -ggdb -fprofile-arcs -ftest-coverage
else
AM_CFLAGS += -O2
endif

if USE_JEMALLOC
AM_LDFLAGS += -ljemalloc
endif

r3_includedir = $(includedir)/r3
r3_include_HEADERS = \
	include/memory.h \
	include/r3.h \
	include/r3_list.h \
	include/r3_slug.h \
	include/r3_gvc.h \
	include/r3_json.h \
	include/str_array.h \
	include/r3.hpp \
	$(NULL)

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = r3.pc

EXTRA_DIST = \
	autogen.sh \
	bench.html \
	demo.c \
	gen_routes.rb \
	HACKING.md \
	LICENSE \
	README.md \
	$(NULL)
