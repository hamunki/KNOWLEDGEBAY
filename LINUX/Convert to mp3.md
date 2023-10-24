Convert to mp3 in Terminal
==========================

* `for f in *.mp4 ; do ffmpeg -i "$f" -acodec libmp3lame -q:a 2 "${f%.*}.mp3"; done`

* `for f in *.webm ; do ffmpeg -i "$f" -acodec libmp3lame -q:a 2 "${f%.*}.mp3"; done`

* `for f in *.png ; do convert -resize 50% "$f" "${f%.*}.png" ; done`

* `for f in *.wav ; do ffmpeg -i "$f" -acodec libmp3lame -q:a 2 "${f%.*}.mp3"; done`


* `convert -resize 50% "$f" "${f%.*}.png" `

* `for f in *.MOV ; do ffmpeg -i "$f" -acodec libmp3lame -q:a 2 "${f%.*}.webm"; done`

* `for f in *.webm ; do ffmpeg -i "$f" -acodec libmp3lame -q:a 2 "${f%.*}.mp4"; done`

* `for f in *.png ; do tesseract "/home/goatfarm/Documents/CLEAR_UP_SCANS/LAUGHTER_BOOK/SCANS/$f" "/home/goatfarm/Documents/CLEAR_UP_SCANS/LAUGHTER_BOOK/OCR/${f%.*}" --dpi 300; done`




* `for f in *.webm ; do ffmpeg -i "$f" -acodec libmp3lame -q:a 2 "${f%.*}.wav"; done`
* `for f in *.mkv ; do ffmpeg -i "$f" -acodec libmp3lame -q:a 2 "${f%.*}.wav"; done`



* `for SONG in *.mp3 ; do mp3tag -s "$SONG" -a "BitesizeJapanese" -l "BitesizeJapanese" "$SONG" ; done`


* `for SONG in *.mp3 ; do id3v2 -t "$SONG" "$SONG" ; done`


---

* `for f in *.wav ; do ffmpeg -i "$f" -acodec libmp3lame -q:a 2 "${f%.*}.ogg"; done`
* `oggenc -q 3 -o file.ogg file.wav`

---