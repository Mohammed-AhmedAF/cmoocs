CC = gcc
SRC = main.c func.c
CFLAGS = -I ../include_test

%.o : $(SRC)
	$(CC) $(SRC) -o $@ $(CFLAGS)

.phony : clean
	rm  *.c
