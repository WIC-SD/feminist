MAIN = main
TEMP = .temp
IGNORE = aux bbl bcf blg fdb_latexmk fls idx ilg ind log out nav run.xml snm toc xdv
FLAG = trash.on


.PHONY: snapshot
snapshot:
	make _untempize
	xelatex $(MAIN)
	make _tempize

.PHONY: tex
tex:
	make _untempize
	latexmk -xelatex $(MAIN)
	make _tempize

.PHONY: clean
clean: _mkdir
	latexmk -c
	rm -r $(TEMP)

.PHONY: _tempize
_tempize: _mkdir
	for temp in $(IGNORE); \
	do \
		if [ -f $(MAIN).$$temp ]; then mv $(MAIN).$$temp $(TEMP)/; fi; \
	done
	mv $(FLAG) $(TEMP)

.PHONY: _untempize
_untempize: _mkdir
	touch $(TEMP)/$(FLAG)
	mv $(TEMP)/* ./

.PHONY: _mkdir
_mkdir:
	mkdir -p $(TEMP)
