PREFIX  := /usr/local
CC      := cc
#CFLAGS  := -pedantic -Wall -Wno-deprecated-declarations -Os
CFLAGS   := -std=c99 -march=native -ftree-vectorize -O3 -msse3 -ftracer -fipa-cp -fipa-pta -funroll-loops -floop-interchange -floop-strip-mine -fgcse-after-reload -finline-functions -pipe -pedantic -Wall -Wno-unused-function -Wno-deprecated-declarations -fcf-protection -fpie -fstack-clash-protection -D_FORTIFY_SOURCE=3 -fpic ${INCS} ${CPPFLAGS}
LDFLAGS := -lX11

# FreeBSD (uncomment)
#LDFLAGS += -L/usr/local/lib -I/usr/local/include
# # OpenBSD (uncomment)
#LDFLAGS += -L/usr/X11R6/lib -I/usr/X11R6/include

all: options dwmblocks

options:
	@echo dwmblocks build options:
	@echo "CFLAGS  = ${CFLAGS}"
	@echo "LDFLAGS = ${LDFLAGS}"
	@echo "CC      = ${CC}"

dwmblocks: dwmblocks.c blocks.def.h blocks.h
	${CC} -o dwmblocks dwmblocks.c ${CFLAGS} ${LDFLAGS}

blocks.h:
	cp blocks.def.h $@

clean:
	rm -f *.o *.gch dwmblocks

install: dwmblocks
	mkdir -p ${DESTDIR}${PREFIX}/bin
	cp -f dwmblocks ${DESTDIR}${PREFIX}/bin
	chmod 755 ${DESTDIR}${PREFIX}/bin/dwmblocks

uninstall:
	rm -f ${DESTDIR}${PREFIX}/bin/dwmblocks

.PHONY: all options clean install uninstall
