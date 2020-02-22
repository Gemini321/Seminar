# Notes of Makefile

## How does it work

1. Input 'make' instruction, and it will try to find a 'Makefile'
2. If there is a 'Makefile' or 'makefile', it will try to find 'edit', and determinate it/them as object file(s)
3. If 'edit' is not found, or the files that 'edit' depends are newer than 'edit', it will execute the following instructions to make the 'edit' files
4. If the dependent files of 'edit' are not existent, it will try to find the dependent files of these files (like a stack)
5. Finally, start from the first dependent files, and make those target files orderly
6. If one of the dependent file can not be made anyway, makefile stops
7. 'edit' should be replaced by what you want to make finally

## How to write a makefile file

The example is as follows (solution of this homework from Hongzheng Chen)

```
CPP = g++
LIBS = -lglut -lGL -lGLU

.PHONY: all clean
all: test1 test2 test3 test4

test1: mesh.o display1.o (Hint: Here $^ = mesh.o display1.o)
	$(CPP) $^ $(LIBS) -Llib -lstest -o test1

test2: mesh.o display2.o
	$(CPP) $^ $(LIBS) -Llib -lstest -o test2

test3: mesh.o display3.o
	$(CPP) $^ $(LIBS) -Llib -lstest -o test3

test4: mesh.o display4.o
	$(CPP) $^ $(LIBS) -Llib -lstest -o test4

mesh.o: mesh.cpp (Hint: Here $@ = mesh.o, $< = mesh.cpp)
	$(CPP) -Iinclude -c -o $@ $<

display1.o: display.cpp
	$(CPP) -Iinclude -DTEST1 -c -o $@ $<

display2.o: display.cpp
	$(CPP) -Iinclude -DTEST2 -c -o $@ $<

display3.o: display.cpp
	$(CPP) -Iinclude -DTEST3 -c -o $@ $<

display4.o: display.cpp
	$(CPP) -Iinclude -c -o $@ $<

clean:
	-rm *o test1 test2 test3 test4
```

And the basic structure of a makefile file is:

```
macros...

('edit' should be replaced by what you want to make finally)
edit: prerequisites 
    commands

target: prerequisites
    commands

.PHONY: clean
clean:
    rm ...
```

### Explanations

1. Three variables are displayed above:

| Variable |     $@      |           $^            |            $<            |
| :------: | :---------: | :---------------------: | :----------------------: |
| Meaning  | Target file | All the dependent files | The first dependent file |

2. Macros: Macros are usually shown at the beginning of makefile, and cited as $(...) (e.g. CPP = g++, $(CPP) = g++ when cited)
3. Automatically concluding: make can automatically recognize what is needed to be executed to make the target file, so once the target and dependent files are determinated, sometimes we need not to add the commands.

For example:
```
Before:
display.o: display.c stdio.h
    gcc -c -o $< $@

After:
display.o: stdio.h
(display.c is recognized as the dependent file of display.o automatically, so it's left out)
```

4. Commands should follow a \[Tab\]
5. Comments should follow a #
6. Clean: We should always write a clean command at the end of makefile. It can help us clean all the object files and executing files conveniently. Remember to "make clean".
7. .PHONY: Fake target (e.g. .PHONY: clean tells that clean is a label rather than a target, so it will not be made)
8. Commands:

| Command |          -l          |        -I        |         -c          |          -o          |          -E           |        -S        |
| :-----: | :------------------: | :--------------: | :-----------------: | :------------------: | :-------------------: | :--------------: |
| Meaning | Link static libaries | File search path | Compilation (.s->.o) | Assign a target name | Preprocessing (.c->.i) | Assembly (.i->.s) |
| Example |   -lGL(link libGL)   |  -I usr\include  |                     |                      |                       |                  |
