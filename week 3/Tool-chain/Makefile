DISP_SOUR = display.cpp
edit : mesh.o display1.o display2.o display3.o
	g++ display1.o mesh.o -o display1 -lGL -lglut -lGLU -L lib/ -lstest
	g++ display2.o mesh.o -o display2 -lGL -lglut -lGLU -L lib/ -lstest
	g++ display3.o mesh.o -o display3 -lGL -lglut -lGLU -L lib/ -lstest

mesh.o : mesh.cpp
	g++ mesh.cpp -c -o mesh.o -I include/

display1.o display2.o display3.o : $(DISP_SOUR)
	g++ $(DISP_SOUR) -c -o display1.o -DTEST1 -I include/
	g++ $(DISP_SOUR) -c -o display2.o -DTEST2 -I include/
	g++ $(DISP_SOUR) -c -o display3.o -DTEST3 -I include/

.PHONY : clean
clean : 
	-rm display1.o display2.o display3.o mesh.o
