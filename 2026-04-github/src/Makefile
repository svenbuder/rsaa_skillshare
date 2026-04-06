.PHONY: all slides clean check

all: check slides

check:
	@command -v pandoc >/dev/null 2>&1 || (echo "Error: pandoc not found" && exit 1)
	@command -v tectonic >/dev/null 2>&1 || (echo "Error: tectonic not found" && exit 1)

slides:
	pandoc slides.md \
		--template=beamer.tex \
		-t beamer \
		--pdf-engine=xelatex \
		-o ../rsaa-skillshare-2026-04-git-slides.pdf

clean:
	rm -f ../rsaa-skillshare-2026-04-git-slides.pdf

