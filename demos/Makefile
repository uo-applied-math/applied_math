
all : index.html

%.html : %.md
	pandoc -o $@ --self-contained $<
