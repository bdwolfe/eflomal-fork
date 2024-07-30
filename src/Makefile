# This is for the final version
# CFLAGS=-Ofast -march=native -Wall --std=gnu99 -Wno-unused-function -g -fopenmp

# This is more suitable for debugging:

#BW: causes linking issues, since not optimizing the "inline" means they need
# a definition somewhere, which the linker can't find
# CFLAGS=-Og -Wall --std=gnu99 -Wno-unused-function -g -fopenmp

CFLAGS=-O1 -Wall --std=gnu99 -Wno-unused-function -g -fopenmp


LDFLAGS=-lm -lgomp -fopenmp
# -lrt
INSTALLDIR=/usr/local/bin
PYINSTALLDIR=../python/eflomal/bin

all: eflomal

eflomal.o: eflomal.c natmap.c hash.c random.c simd_math_prims.h
	$(CC) $(CFLAGS) -c eflomal.c

eflomal: eflomal.o
	$(CC) $(CFLAGS) eflomal.o -o eflomal $(LDFLAGS)

python-install: eflomal
	mkdir -p $(PYINSTALLDIR)
	cp eflomal $(PYINSTALLDIR)

install: eflomal
	install -t $(INSTALLDIR) eflomal

clean:
	rm -f eflomal eflomal.o

