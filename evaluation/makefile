CFLAGS = -O0 -g3 -Wall -Wextra -pedantic -lboundscheck -lmastik
HITLS_DIR = ../hitls

aes: main.c wrapper.c wrapper.h $(HITLS_DIR)/declarations.h makefile
	$(CC) -o $@ $< wrapper.c -L$(HITLS_DIR)/original/ -lhitls_crypto $(CFLAGS) -DAES

sm4: main.c wrapper.c wrapper.h $(HITLS_DIR)/declarations.h makefile
	$(CC) -o $@ $< wrapper.c -L$(HITLS_DIR)/original/ -lhitls_crypto $(CFLAGS) -DSM4

ARGS ?=

run-aes-%: aes
	@LD_LIBRARY_PATH=$(HITLS_DIR)/$*/:$$LD_LIBRARY_PATH ./aes $(ARGS)

run-sm4-%: sm4
	@LD_LIBRARY_PATH=$(HITLS_DIR)/$*/:$$LD_LIBRARY_PATH ./sm4 $(ARGS)