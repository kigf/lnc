CC=g++
AR=ar
ARFLAGS= rcs
OSTYPE := $(shell uname)

ifeq ($(OSTYPE),Linux)
	CFLAGS=-c -Wall -std=c++17 -Wunreachable-code -fopenmp
	LFLAGS=-fopenmp
	LIBS=
	INCLUDES=-I. 
else
	CFLAGS=-c -Wall -std=c++17 -Wunreachable-code -Xclang -fopenmp
	LFLAGS=
	LIBS=-lomp -L ../../openmp/lib -L /opt/homebrew/lib
	INCLUDES=-I. -I ../../openmp/include -I /opt/homebrew/include
endif

SRC = LA.cpp BPNetwork.cpp InputLayer.cpp NeuralNetwork.cpp ConvolutionLayer.cpp MaxPoolLayer.cpp DenseLayer.cpp SoftmaxLayer.cpp
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

