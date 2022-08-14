#   Copyright (C) 2022  Libre MATE
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301  USA

AC_INIT([mozo],
        [1.26.0],
        [https://github.com/Libre-MATE/mozo/issues],
        [mozo],
        [https://github.com/Libre-MATE/mozo/])
AC_PREREQ(2.53)
AC_COPYRIGHT([Copyright (C) 2022 Libre MATE])
AC_CONFIG_SRCDIR(mozo.in)
AC_CONFIG_HEADERS([config.h])
AM_INIT_AUTOMAKE([1.11 dist-xz no-dist-gzip check-news])
AM_SILENT_RULES([yes])
AM_MAINTAINER_MODE

dnl put the ACLOCAL flags in the makefile
ACLOCAL="$ACLOCAL $ACLOCAL_FLAGS"

GETTEXT_PACKAGE=AC_PACKAGE_NAME
AC_SUBST(GETTEXT_PACKAGE)
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE, "$GETTEXT_PACKAGE", [Gettext package])
AM_GNU_GETTEXT_VERSION([0.19.8])
AM_GNU_GETTEXT_REQUIRE_VERSION([0.19.8])
AM_GNU_GETTEXT([external])

AC_PROG_SED
AM_PATH_PYTHON(3.5)

PKG_CHECK_MODULES(MOZO, libmate-menu >= 1.21.0 pygobject-3.0)

AC_ARG_ENABLE(icon-update, AS_HELP_STRING([--disable-icon-update],
					[Disable icon cache update]))
if (test "$enable_icon_update" != no); then
	AC_PATH_PROG(UPDATE_ICON_CACHE, [gtk-update-icon-cache])
fi
AM_CONDITIONAL([ICON_UPDATE], [test -n "$UPDATE_ICON_CACHE"])

AC_CONFIG_FILES([
        Makefile
        po/Makefile.in
        Mozo/Makefile
        data/mozo.desktop.in
        data/Makefile
        data/icons/Makefile])
AC_OUTPUT

