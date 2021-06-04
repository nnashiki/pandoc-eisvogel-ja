# pandoc-eisvogel-ja

Pandoc + eisvogel で日本語を含む Markdown から PDF 出力できる Dokcer コンテナ

# build

```
cd pandocja
docker build -t pandoc_ja:0.1 .
```

# gen pdf-sammple

```
cd sample
docker run -v ${PWD}:/data -w /data --rm pandoc_ja:0.1 pandoc sample.md \
 --from markdown \
 --number-sections \
 --pdf-engine=lualatex \
 --template eisvogel \
 --variable=documentclass:ltjsarticle \
 --variable=CJKmainfont:IPAexGothic \
 --output=sample.pdf
```

↑ 動かなくなった

```
$ docker run --rm -v $(pwd):/data frozenbonito/pandoc-eisvogel-ja \
    -V luatexjapresetoptions=ipaex \
    -o sample.pdf \
    README.md
```