dnl Process this file with autoconf to produce a configure script.

# Tested with autoconf 2.69, released in 2012
AC_PREREQ([2.69])
AC_INIT(DAW_Demo, [m4_esyscmd_s([echo $VERSION])], support.computing@caen.it)
AC_CONFIG_AUX_DIR([src])
AM_INIT_AUTOMAKE([-Wall foreign subdir-objects tar-ustar])
AC_CONFIG_SRCDIR([inc/DAWDemoFunc.h])
AC_PROG_CC
AC_PROG_INSTALL
AC_DEFINE(LINUX,[1],"Define LINUX")
# Checks for libraries.
AC_CHECK_HEADER(CAENDigitizer.h,[a=0],[a=1])
if test $a == 1; then
        AC_MSG_ERROR([
                CAENDigitizer >= 2.12.0 must be installed on your system.])
fi

AC_CHECK_PROG(GNUPLOT,gnuplot,"ok","no")
if test $GNUPLOT == "no"; then
        AC_MSG_WARN(
	*****************************************************************
    GnuPLot not found PeakSensing_DAQ will be unable to show graphical data.
    *****************************************************************
	)
fi

AC_CONFIG_FILES(Makefile src/Makefile)
AC_OUTPUT

