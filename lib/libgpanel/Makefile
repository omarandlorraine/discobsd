TOPSRC!=cd ../..; pwd
include $(TOPSRC)/target.mk

CFLAGS          += -O -Wall
MAN             = gpanel.0
MANSRC          = gpanel.3

OBJS    	= open.o clear.o pixel.o line.o rect.o fill.o fill_triangle.o \
                  circle.o image.o char.o text.o text_width.o

all:    	../libgpanel.a $(MAN)

../libgpanel.a: ${OBJS}
		@$(AR) cru $@ ${OBJS}
		$(RANLIB) $@

$(MAN):         $(MANSRC)
		${MANROFF} ${MANSRC} > $@

install: 	all
		cp ${MAN} ${DESTDIR}/usr/share/man/cat3/

clean:
		rm -f *.o a.out core test errs ../libgpanel*.a $(MAN)
