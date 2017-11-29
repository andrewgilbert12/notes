calc: calc.y calc.l
  yacc -d calc.y # emits y.tab.h, y.tab.c
  lex calc.l # emits lex.yy.c
  gcc lex.yy.c y.tab.c -o calc # links and compiles
  rm lex.yy.c y.tab. # clean up intermediate files
