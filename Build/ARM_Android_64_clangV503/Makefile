# Makefile

#==============================================================================
# ARM Aarch64 Android, LLVM clang
#------------------------------------------------------------------------------
CC = clang -m64 -pthread
OPTIONS = -O3 -fPIC
#==============================================================================

MATH = -lm

all: cflp_udf.o fastlisp BMDFMldr BMDFMsrv CPUPROC

cflp_udf.o: cflp_udf.c cflp_udf.h
	$(CC) $(OPTIONS) -c cflp_udf.c

fastlisp: fastlisp.o cflp_udf.o
	$(CC) -pie -o fastlisp fastlisp.o cflp_udf.o $(MATH)

BMDFMldr: BMDFMldr.o cflp_udf.o
	$(CC) -pie -o BMDFMldr BMDFMldr.o cflp_udf.o $(MATH)

BMDFMsrv: BMDFMsrv.o cflp_udf.o
	$(CC) -pie -o BMDFMsrv BMDFMsrv.o cflp_udf.o $(MATH)

CPUPROC: CPUPROC.o cflp_udf.o
	$(CC) -pie -o CPUPROC CPUPROC.o cflp_udf.o $(MATH)

clean:
	rm -f cflp_udf.o fastlisp BMDFMldr BMDFMsrv CPUPROC 2>/dev/null

