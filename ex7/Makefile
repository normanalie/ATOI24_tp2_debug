CC=clang
CFLAGS=-pthread -Wall -g

all: program

program: lock.o
	$(CC) $(CFLAGS) -o program lock.o

lock.o: lock.c
	$(CC) $(CFLAGS) -c lock.c

clean:
	rm -f *.o program
