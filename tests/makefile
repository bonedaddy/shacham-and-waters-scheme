CC = gcc
CFLAGS = -std=gnu99
INCLUDES = -I ../include/
LIBS = -lrs -lgmp -lpbc

SRCS := reed-solomon.c 	file_block.c	file_encode.c 	write_test.c 	\
		log_tests.c 	sha2_tests.c	blstest.c		audit_tests.c	\
		file_elem.c		hmac_test.c		port_tests.c
OBJS := $(SRCS:.c=.o)

.PHONY: clean

VPATH = ../lib

all: $(OBJS) $(SRCS) makefile

$(OBJS): print-utils.c logging.c

reed-solomon.o: 	reed-solomon.c
file_block.o: 		handlefile.c file_block.c
file_encode.o: 		handlefile.c file_encode.c
write_test.o: 		handlefile.c write_test.c
log_tests.o: 		log_tests.c
sha2_tests.o: 		sha256.c sha2_tests.c
blstest.o: 			bls.c blstest.c
audit_tests.o:		audit_tests.c handlefile.c audit.c bls.c port.c
file_elem.o:		file_elem.c bls.c handlefile.c
hmac_test.o:		hmac_test.c hmac-sha256.c sha256.c
port_tests.o:		port_tests.c port.c handlefile.c audit.c bls.c

$(OBJS) :
	@$(CC) $(CFLAGS) $(INCLUDES) $^ -o $@ $(LIBS)
	@./$@ ../LICENSE

clean: 
	rm -f *.o