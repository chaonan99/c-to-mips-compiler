bin/c_compiler: src/c_bison.tab.o src/c_lexer.yy.o
	g++ -std=gnu++11 src/c_bison.tab.o src/c_lexer.yy.o -o bin/c_compiler && chmod +x bin/c_compiler

src/c_lexer.yy.o: src/c_lexer.yy.c src/c_bison.tab.h
	g++ -std=gnu++11 -c src/c_lexer.yy.c && mv c_lexer.yy.o src/

src/c_bison.tab.o: src/c_bison.tab.c src/c_bison.tab.h
	g++ -std=gnu++11 -c src/c_bison.tab.c && mv c_bison.tab.o src/

src/c_bison.tab.c : src/c_bison.y
	bison -d src/c_bison.y && mv c_bison.tab.c src/

src/c_bison.tab.h: src/c_bison.y
	bison -d src/c_bison.y && mv c_bison.tab.h src/

src/c_lexer.yy.c: src/c_lexer.l
	flex -o src/c_lexer.yy.c src/c_lexer.l

clean :
	rm src/c_lexer.yy.c src/c_bison.tab.c src/c_bison.tab.h
	rm bin/c_compiler
	rm src/*.o 
