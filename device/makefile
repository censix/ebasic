CC=e-gcc
CFLAGS=-I ../ -I ../interpreter -O1 -Os
LDFLAGS=-T ${EPIPHANY_HOME}/bsps/current/fast.ldf -Wl,--gc-sections

ebasic-device: main.o device-functions.o ../interpreter/interpreter.o
bins = ebasic-device

.PHONE: check

%.o : %.c
	$(CC) $(CFLAGS) -MMD -o $@ -c $<

$(bins) :
	$(CC) $(LDFLAGS) -o $@ $^ $(LIBS) -le-lib
	e-objcopy --srec-forceS3 --output-target srec ebasic-device ebasic-device.srec

clean:
	$(RM) -f -v $(bins) *.yy.[ch] *.tab.[ch] *.o *.d *.output

-include *.d
