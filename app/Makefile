JVM = java
JC = javac
.SUFFIXES : .java .class
%.class: 
	  $(JC) $(MODULES) $*.java
	  $(JVM) $(MODULES) $(PACKAGE).$(MAIN)
PACKAGE = sample
CLASSES = \
	sample/Controller.java\
	sample/Parser.java\
	sample/Main.java\
	sample/Transaction.java\
	sample/Relation.java\
	sample/ElementVisuel.java\

MAIN = Main
MODULES = --module-path lib/ --add-modules=javafx.controls,javafx.fxml
DOT = /usr/bin/dot



checkJava: 
ifeq ($(shell java --version 2>&1|grep "openjdk 14" >/dev/null; printf $$?),0)
	@make checkDOT
else
	$(error "Could not find correct java version, please install 14")
endif

all : checkJava clean
compile :	
	$(JC) $(MODULES) $(PACKAGE)/*.java
run :
	$(JVM) $(MODULES) $(PACKAGE).$(MAIN)
clean :
	$(RM) $(PACKAGE)/*.class

checkDOT : 
ifeq ($(shell command -v dot 2>&1 | grep dot >/dev/null; printf $$?),0)
	@make clean
	@make compile
	@make run
else
	$(error "dot is not available, please install graphviz")	
endif