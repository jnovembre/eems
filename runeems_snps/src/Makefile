# BOOST_LIB     = /usr/local/lib
# BOOST_INCLUDE = /usr/local/include
# EIGEN_INCLUDE = /usr/local/opt/eigen/include/eigen3
BOOST_LIB     = $(SCRATCH)/boost-1.57.0/lib
BOOST_INCLUDE = $(SCRATCH)/boost-1.57.0/include
EIGEN_INCLUDE = $(HOME)/eigen-3.2.2

OBJ = runeems_snps.o eems.o util.o mcmc.o draw.o habitat.o graph.o

CXX      = g++
CXXFLAGS = -I$(BOOST_INCLUDE) -I$(EIGEN_INCLUDE) -O3
LDFLAGS  = -lboost_system -lboost_program_options -lboost_filesystem

all: runeems_snps

runeems_snps: $(OBJ)
	$(CXX) $(CXXFLAGS) -o $@ $^ -L$(BOOST_LIB) $(LDFLAGS)

%.o: %.cpp
	$(CXX) $(CXXFLAGS) -c $<

clean:
	rm -f runeems_snps $(OBJ)


