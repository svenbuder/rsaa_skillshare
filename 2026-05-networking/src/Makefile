.PHONY: all slides worksheet clean check

all: check slides worksheet

check:
	@command -v pandoc >/dev/null 2>&1 || (echo "Error: pandoc not found" && exit 1)
	@command -v tectonic >/dev/null 2>&1 || (echo "Error: tectonic not found" && exit 1)

slides:
	pandoc slides.md \
		--template=template_beamer.tex \
		-t beamer \
		--pdf-engine=xelatex \
		-o ../rsaa-skillshare-2026-05-networking.pdf

worksheet:
	pandoc worksheet.md \
		--template=template_worksheet.tex \
		--pdf-engine=xelatex \
		-o ../rsaa-skillshare-2026-05-networking_worksheet.pdf

clean:
	rm -f ../rsaa-skillshare-2026-05-networking.pdf ../rsaa-skillshare-2026-05-networking_worksheet.pdf

