TOPSRC!=cd ../..; pwd
include $(TOPSRC)/target.mk

CFLAGS          += -Wall -Os

virus:          virus.c
		$(CC) $(LDFLAGS) -o virus.elf virus.c $(LIBS) -ltermcap
		$(SIZE) virus.elf
		$(ELF2AOUT) virus.elf $@

install:        virus
		install virus ${DESTDIR}/usr/bin/vi

clean:
		rm -f *.o virus.elf virus
