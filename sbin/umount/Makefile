#
# Public Domain.  1996/1/15 - Steven Schultz
#
TOPSRC!=cd ../..; pwd
include $(TOPSRC)/target.mk

SRCS		= umount.c
OBJS		= umount.o
MAN		= umount.0
MANSRC		= umount.8

all:            umount umount.0

umount:         ${OBJS}
		${CC} ${LDFLAGS} -o umount.elf ${OBJS} ${LIBS}
		${OBJDUMP} -S umount.elf > umount.dis
		${SIZE} umount.elf
		${ELF2AOUT} umount.elf $@ && rm umount.elf

umount.0:       ${MANSRC}
		${MANROFF} ${MANSRC} > ${MAN}

clean:
		rm -f *.o *.elf ${MAN} umount *.elf *.dis tags *~

depend:         ${SRCS}
		mkdep ${CFLAGS} ${SRCS}

install:        all
		cp ${MAN} ${DESTDIR}/usr/share/man/cat8/
		install umount ${DESTDIR}/sbin/umount

lint:           ${SRCS}
		lint -hax ${SRCS}

tags:           ${SRCS}
		ctags ${SRCS}

# DO NOT DELETE THIS LINE -- mkdep uses it.
# DO NOT PUT ANYTHING AFTER THIS LINE, IT WILL GO AWAY.
