.PHONY: all slides worksheet clean check

all: check slides worksheet

check:
	@command -v pandoc >/dev/null 2>&1 || (echo "Error: pandoc not found" && exit 1)
	@command -v tectonic >/dev/null 2>&1 || (echo "Error: tectonic not found" && exit 1)

slides:
	pandoc intro-slides.md \
		--template=template/beamer.tex \
		-t beamer \
		--pdf-engine=xelatex \
		-o ../rsaa-skillshare-2026-02-intro-slides.pdf

worksheet:
	pandoc worksheet.md \
		--template=template/worksheet.tex \
		--pdf-engine=xelatex \
		-o ../rsaa-skillshare-2026-02-worksheet.pdf

clean:
	rm -f ../intro-slides.pdf ../worksheet.pdf

