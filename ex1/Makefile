# Compilateur
CC = gcc

# Options de compilation
CFLAGS = -Wall -Wextra -std=c99

# Fichiers source
SRCS = main.c ppm.c

# Nom de l'exécutable
EXEC = a.out

# Fichiers objet
OBJS = $(SRCS:.c=.o)

# Règle de construction de l'exécutable
$(EXEC): $(OBJS)
	$(CC) $(CFLAGS) -o $@ $^

# Règle de compilation des fichiers source
%.o: %.c
	$(CC) $(CFLAGS) -c -o $@ $<

# Nettoyage des fichiers temporaires
clean:
	rm -f $(OBJS) $(EXEC)
