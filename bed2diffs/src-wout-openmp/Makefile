# A Makefile for generating the bed2diffs executable (static or
# dynamic) from the C++ source.
#
# To use this Makefile, you will need to adjust some of the settings
# below to meet your computing environment.

# Default file paths:
PLINKIO_LIB     = /usr/local/lib
PLINKIO_INCLUDE = /usr/local/include

# The paths we used on the midway2 cluster:
#
#  PLINKIO_LIB     = $(SCRATCH)/libplinkio-0.3.1/lib
#  PLINKIO_INCLUDE = $(SCRATCH)/libplinkio-0.3.1/include
#

# By default, a dynamic executable is created. In a Linux environment,
# you may add the "-static" option to LDFLAGS to compile a statically
# linked binary executable. In a macOS environment, statically linked
# libraries are not supported, but we can at least link to the static
# versions of the Boost libraries with the following settings:
#
#   LDFLAGS = $(PLINKIO_LIB)/libplinkio.a
#
CXX      = g++
CXXFLAGS = -I${PLINKIO_INCLUDE} -O3
LDFLAGS  = -lplinkio

OBJ = bed2diffs_v1.o data.o

all: bed2diffs_v1

bed2diffs_v1: $(OBJ)
	$(CXX) $(CXXFLAGS) -o $@ $^ -L$(BOOST_LIB) $(LDFLAGS)

%.o: %.cpp
	$(CXX) $(CXXFLAGS) -c $<

clean:
	rm -f bed2diffs_v1 $(OBJ)

# ----------------------------------------------------

CXXFLAGS = -I${PLINKIO} -O3
