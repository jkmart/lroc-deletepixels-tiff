# User defined parameters
CC = gcc
CFLAGS = -Wall --pedantic --std=gnu99
CDEFINES = HAVE_UNISTD_H
LIBS = -lm
SRCS = deletepixels.c
EXECUTABLE = deletepixels

OS = $(shell uname)

ifeq ($(OS), Darwin) # Mac OS
SLIBDIR = ../libs/osx
else ifeq ($(OS), Linux) # Linux
SLIBDIR = ../libs/linux
endif

SLIBS = $(SLIBDIR)/bigtiff.a $(SLIBDIR)/libjpeg.a $(SLIBDIR)/libz.a
OBJS = $(SRCS:.c=.o) $(SLIBS)

.PHONY: all clean

all: $(EXECUTABLE)

$(EXECUTABLE): $(OBJS)
	$(CC) $(CFLAGS) -D$(CDEFINES) -o $(EXECUTABLE) $(OBJS) $(LIBS)

.c.o:
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	$(RM) *.o *~ $(EXECUTABLE)
