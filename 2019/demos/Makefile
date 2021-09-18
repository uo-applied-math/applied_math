
all : index.html configuration_process.html random_spanning_tree.html 

%.html : %.md
	pandoc -o $@ --self-contained $<

%.html : %.ipynb 
	jupyter nbconvert --to html $<

