
AM_CPPFLAGS =								\
	-I$(top_builddir)						\
	-I$(top_builddir)/plugins					\
	-I$(top_srcdir)							\
	-I$(top_srcdir)/plugins						\
	-DG_LOG_DOMAIN=\"libthunar-tpa\"				\
	$(PLATFORM_CPPFLAGS)

plugindir = $(libdir)/xfce4/panel/plugins
plugin_LTLIBRARIES =							\
	libthunar-tpa.la

libthunar_tpa_la_SOURCES =						\
	thunar-tpa.c							\
	thunar-tpa-bindings.h

libthunar_tpa_la_CFLAGS =						\
	$(DBUS_CFLAGS)							\
	$(LIBXFCE4UI_CFLAGS)						\
	$(LIBXFCE4UTIL_CFLAGS)						\
	$(LIBXFCE4PANEL_CFLAGS)						\
	$(PLATFORM_CFLAGS)

libthunar_tpa_la_LIBADD =						\
	$(DBUS_LIBS)							\
	$(LIBXFCE4UTIL_LIBS)						\
	$(LIBXFCE4UI_LIBS)						\
	$(LIBXFCE4PANEL_LIBS)

libthunar_tpa_la_LDFLAGS =						\
	-avoid-version							\
	-module								\
	-no-undefined							\
	-export-symbols-regex '^xfce_panel_module_(preinit|init|construct)' \
	$(PLATFORM_LDFLAGS)

desktopdir = $(datadir)/xfce4/panel/plugins
desktop_in_files = thunar-tpa.desktop.in
desktop_DATA = $(desktop_in_files:.desktop.in=.desktop)
@INTLTOOL_DESKTOP_RULE@

if MAINTAINER_MODE
BUILT_SOURCES =								\
	thunar-tpa-bindings.h

DISTCLEANFILES =							\
	thunar-tpa-bindings.h

thunar-tpa-bindings.h: $(srcdir)/thunar-tpa-bindings.xml Makefile
	$(AM_V_GEN) dbus-binding-tool --prefix=thunar_tpa_dbus --mode=glib-client $(srcdir)/thunar-tpa-bindings.xml > thunar-tpa-bindings.h
endif

EXTRA_DIST =								\
	$(desktop_in_files)						\
	thunar-tpa-bindings.xml						\
	README

CLEANFILES =								\
	$(desktop_DATA)

# vi:set ts=8 sw=8 noet ai nocindent syntax=automake:
