# pandoc-eisvogel-ja

こちらの repo の dockerfile が動かなくなったので、以下のコマンドでpdfをbuildしてください。

```
$ docker run --rm -v $(pwd):/data frozenbonito/pandoc-eisvogel-ja \
    -V luatexjapresetoptions=ipaex \
    -o sample.pdf \
    README.md
```
