# Use this variable to customize the LAPACK to include. Here is an example
# that matches the configuration used in the paper
#
# Fast Hessenberg Reduction for some rank structured matrices,
# L. Gemignani and L.Robol, https://arxiv.org/abs/1612.04196
#
# LAPACK = /path/to/lapack-3.6.1/build/lib/liblapack.a \
#          /path/to/lapack-3.6.1/build/lib/libblas.a

LAPACK = -llapack -lblas

CFLAGS = -O2

all: test_runtime hessenberg_reduction test_rank

test_runtime: test_runtime.f90 cdslib.f90 hr_impl_full_to_kh.f90
	f95 $(CFLAGS) -o test_runtime test_runtime.f90 hr_impl_full_to_kh.f90 cdslib.f90 $(LAPACK)

test_rank: test_rank.f90 cdslib.f90 hr_impl_full_to_kh.f90
	f95 $(CFLAGS) -o test_rank test_rank.f90 hr_impl_full_to_kh.f90 cdslib.f90 $(LAPACK)

hessenberg_reduction: hessenberg_reduction.f90
	f95 $(CFLAGS) -o hessenberg_reduction hessenberg_reduction.f90 $(LAPACK)


clean:
	rm -f test_runtime hessenberg_reduction test_rank
