extra_libs =

if OS_ANDROID
extra_libs += \
	$(top_builddir)/lib/selinux/libfrida-selinux.la \
	-llog
endif

bin_PROGRAMS = frida-server

frida_server_SOURCES = \
	server.vala \
	server-glue.c
frida_server_CFLAGS = \
	-w
frida_server_LDFLAGS = \
	$(FRIDA_LDFLAGS)
frida_server_LDADD = \
	$(top_builddir)/src/libfrida-core-1.0.la \
	$(FRIDA_LIBS) \
	$(extra_libs)
frida_server_VALAFLAGS = \
	--library=frida-server \
	--header=frida-server.h \
	--vapidir=$(abs_top_srcdir)/vapi \
	--vapidir=$(abs_top_srcdir)/lib/interfaces \
	--vapidir=$(abs_top_srcdir)/src \
	--pkg=config \
	--pkg=frida-interfaces \
	--pkg=frida-core \
	@FRIDA_PACKAGES@ \
	@FRIDA_VALAFLAGS@

AM_CPPFLAGS = \
	-DG_LOG_DOMAIN=\"Frida\" \
	-include config.h \
	-I $(top_srcdir)/lib/selinux/include \
	-I $(top_srcdir)/lib/interfaces \
	-I $(top_srcdir)/src \
	$(FRIDA_CFLAGS)
