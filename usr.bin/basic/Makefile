TOPSRC!=cd ../..; pwd
include $(TOPSRC)/target.mk
#include $(TOPSRC)/cross.mk

CFLAGS		+= -Wall

OBJS            = basic.o

LIBS		= -lcurses -ltermcap -lm -lc

all:            basic renumber

basic:          ${OBJS}
		${CC} ${LDFLAGS} -o basic.elf ${OBJS} ${LIBS}
		${OBJDUMP} -S basic.elf > basic.dis
		${SIZE} basic.elf
		${ELF2AOUT} basic.elf $@ && rm basic.elf

renumber:       renumber.o
		${CC} ${LDFLAGS} -o renumber.elf renumber.o ${LIBS}
		${OBJDUMP} -S renumber.elf > renumber.dis
		${SIZE} renumber.elf
		${ELF2AOUT} renumber.elf $@ && rm renumber.elf

clean:
		rm -f *.o basic renumber *.elf *.dis *~

install:        all
		install basic ${DESTDIR}/usr/bin/
		install renumber ${DESTDIR}/usr/bin/
