#
# makefile
#
CC = gcc
CFLAGS = -m64 -pthread
SRCS = $(wildcard 9.*.c)
PROGS = $(patsubst %.c,%,$(SRCS))
PROGS_TEST = $(patsubst %.c,%.test,$(SRCS))

all: $(PROGS)
	(cd vm; make)
	(cd malloc; make)

%: %.c
	$(CC) $(CFLAGS) -o $@ $< vm/csapp.c

test: $(PROGS_TEST)
	(cd vm; make test)
	(cd malloc; make test)

%.test: %
	./$<

.PHONY : clean
clean:
	(cd vm; make clean)
	(cd malloc; make clean)
	find . -type f -executable -print0 | xargs -0 rm -f --
