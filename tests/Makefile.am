# TOPSRCDIR allows to compile this testsuite for a clone (and different revision) of this
# repository. If the environment variable topsrcdir is the top source directory of the clone,
# compile this testsuite as:
#
# make TOPSRCDIR="$topsrcdir"
#
# Finally, if you also leave out TOPSRCDIR and just run 'make' then the testsuite
# is compiled against the current source tree.

AUTOMAKE_OPTIONS = foreign
TOPSRCDIR = $(srcdir)/..
TOPBUILDDIR = $(builddir)/..
DEFINES =
# include TOPBUILDIR for m4ri_config.h
AM_CFLAGS = -I$(TOPSRCDIR) -I$(TOPBUILDDIR) -iquote$(TOPBUILDDIR)/m4ri -D_XOPEN_SOURCE=600 $(DEFINES) @OPENMP_CFLAGS@ @PAPI_CFLAGS@ @LIBPNG_CFLAGS@

STAGEDIR := $(realpath -s $(TOPBUILDDIR)/.libs)
AM_LDFLAGS = -Wl,-rpath,$(STAGEDIR) $(LIBM) @PAPI_LDFLAGS@ @PAPI_LIBS@ @M4RI_INSTALL_FLAGS@

LDADD = $(TOPBUILDDIR)/libm4ri.la

test_smallops_SOURCES = test_smallops.c testing.c testing.h

TESTS = test_elimination \
	test_multiplication \
	test_trsm \
	test_ple \
	test_pluq \
	test_solve \
	test_kernel \
	test_random \
	test_smallops \
	test_transpose \
	test_colswap \
	test_misc \
	test_invert \
	test_alignment \
	test_djb

check_PROGRAMS = $(TESTS)

