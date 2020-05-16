#
# Project: Hello ASM
#
# File: Makefile
#
# Programmer: Joseph Osborne
# Date Created: 05/16/2020
#
# ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~.
PROJECT_ROOT	= ./#../../../
LIBDIR			= $(PROJECT_ROOT)lib
BIN				= $(PROJECT_ROOT)bin
INCLUDE			= $(PROJECT_ROOT)include
# ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~.
# Program to make (binary) 'HelloWorld'
EXECUTABLE		= hello
# Source files for EXECUTABLE/LIBRARY
SRC				= hello.s
# LIBS needed to compile the EXECUTABLE (use LIBDIR as needed)
LIBS			= 
# How they are invoked on the compile line (eg: -lspecial)
LLIBS			=
# ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~.
CFLAGS			= -I $(INCLUDE) -no-pie
CC				= gcc $(CFLAGS)
OBJ		 		= $(SRC:.c=.o)
# ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~.
.PHONY: install it clean depends stripped opto

.c.o:
	$(CC) -c $<

it: $(EXECUTABLE)

stripped:
	$(CC) -s $(SRC) -o $(EXECUTABLE)_stripped

opto:
	$(CC) -s $(SRC) -O3 -o $(EXECUTABLE)_opto

install: $(BIN)/$(EXECUTABLE)
$(BIN)/$(EXECUTABLE): $(EXECUTABLE)
	install -c -s -m 755 $(EXECUTABLE) $(BIN)

$(LIBRARY): $(OBJ)
	ar rcs $@ $^

$(EXECUTABLE): $(OBJ) $(LIBS)
	$(CC) $(OBJ) $(LIBS) $(LLIBS) -o $(EXECUTABLE)
	chmod 755 $(EXECUTABLE)	

$(SRC):
	co $@

clean:
	rm -f core a.out mon.out gmon.out $(EXECUTABLE) $(EXECUTABLE)_stripped $(EXECUTABLE)_opto

depend: $(SRC)
	cc -M $(CFLAGS) $(SRC) > dependlist
	sed -e '1,/^# DO NOT DELETE/!d' Makefile > /tmp/m.tmp
	cat dependlist >> /tmp/m.tmp
	mv /tmp/m.tmp Makefile
	rm -f dependlist

# ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~. ~.~.

# DO NOT DELETE THIS LINE - make depend needs it # 
