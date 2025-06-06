SRC := $(wildcard *.c)

# Output object files with arch suffixes
OBJS_x64 := $(patsubst %.c, %.x64.o, $(SRC))
OBJS_x86 := $(patsubst %.c, %.x86.o, $(SRC))

CC_x64 := x86_64-w64-mingw32-gcc
STRIP_x64 := x86_64-w64-mingw32-strip

CC_x86 := i686-w64-mingw32-gcc
STRIP_x86 := i686-w64-mingw32-strip

all: $(OBJS_x64) $(OBJS_x86)

# x64 build rule
%.x64.o: %.c
	$(CC_x64) -o $@ -c $< -masm=intel -Wall
	$(STRIP_x64) --strip-unneeded $@

# x86 build rule
%.x86.o: %.c
	$(CC_x86) -o $@ -c $< -masm=intel -Wall
	$(STRIP_x86) --strip-unneeded $@

clean:
	rm -f *.x64.o *.x86.o