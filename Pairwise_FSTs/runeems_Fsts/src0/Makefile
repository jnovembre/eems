# A Makefile for generating the runeems_Fsts executable (static or
# dynamic) from the C++ source.
#
# To use this Makefile, you will need to adjust some of the settings
# below to meet your computing environment

# Default file paths for the Boost and Eigen libraries:
BOOST_LIB     = /usr/local/lib
BOOST_INCLUDE = /usr/local/include
EIGEN_INCLUDE = /usr/local/opt/eigen/include/eigen3

# Boost and Eigen library paths we used on the midway2 cluster:
#
#  BOOST_LIB     = $(SCRATCH)/boost-1.57.0/lib
#  BOOST_INCLUDE = $(SCRATCH)/boost-1.57.0/include
#  EIGEN_INCLUDE = $(SCRATCH)/eigen-3.2.2
# 
# Boost and Eigen library paths we used on a MacBook Pro:
#
#  BOOST_LIB     = $(HOME)/boost-1.57.0/lib
#  BOOST_INCLUDE = $(HOME)/boost-1.57.0/include
#  EIGEN_INCLUDE = $(HOME)/eigen-3.2.2
#

# By default, a dynamic executable is created. In a Linux environment,
# you may add the "-static" option to LDFLAGS to compile a statically
# linked binary executable. In a macOS environment, statically linked
# libraries are not supported, but we can at least link to the static
# versions of the Boost libraries with the following settings:
#
#   LDFLAGS = $(BOOST_LIB)/libboost_system.a \
#             $(BOOST_LIB)/libboost_program_options.a \
#             $(BOOST_LIB)/libboost_filesystem.a
#
CXX      = g++
CXXFLAGS = -I$(BOOST_INCLUDE) -I$(EIGEN_INCLUDE) -O3
LDFLAGS  = -lboost_system -lboost_program_options \
           -lboost_filesystem

OBJ = runeems_Fsts_v0.o eems.o util.o mcmc.o draw.o habitat.o graph.o

all: runeems_Fsts_v0

runeems_Fsts_v0: $(OBJ)
	$(CXX) $(CXXFLAGS) -o $@ $^ -L$(BOOST_LIB) $(LDFLAGS)

%.o: %.cpp
	$(CXX) $(CXXFLAGS) -c $<

clean:
	rm -f runeems_Fsts_v0 $(OBJ)

