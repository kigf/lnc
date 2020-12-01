CC=g++
AR=ar
ARFLAGS= rcs
CFLAGS=-c -Wall -std=c++17 -Wunreachable-code -Xclang -fopenmp
LFLAGS=
LIBS=-lomp -L ../../openmp/lib
INCLUDES=-I. -I ../../openmp/include
SRC = LA.cpp BPNetwork.cpp
OBJ = $(SRC:.cpp=.o)
TARGET = libml.a

all: $(TARGET)

release: CFLAGS += -O3 -DNDEBUG
release: $(TARGET)

$(TARGET): $(OBJ)
	$(AR) $(ARFLAGS) $@ $^

%.o: %.cpp
	$(CC) $(CFLAGS) $(INCLUDES) $^ -o $@

clean:
	-rm -rf $(OBJ) $(TARGET) core
