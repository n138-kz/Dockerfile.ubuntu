# README

```bash
docker build \
  --progress=plain \
  --no-cache \
  -t n138-kz/ubuntu:latest \
  -t n138-kz/ubuntu:lts-latest \
  -t n138-kz/ubuntu:2404 \
  -t n138-kz/ubuntu:24.04 \
  -t n138-kz/ubuntu:24.04-lts \
  .
```

```bash
docker run --rm -it n138-kz/ubuntu:2404
```

---

## [Ubuntu18.04でHEIC形式の画像ファイルをJPG、PNG形式に変換するための手順](https://virment.com/install-libheif-to-convert-heic-to-jpg/)

```bash
apt install -y libheif-examples
rename -v 's/.HEIC/heic/g' *.HEIC
for i in *.heic; do heif-convert "${i}" "${i%.heic}.jpg"; test -d _trash || mkdir _trash; mv "${i}" _trash; done
rename -v 's/:/_/g' *.jpg
```

## yt-dlp

```sh
curl -L https://github.com/yt-dlp/yt-dlp/releases/download/2025.01.26/yt-dlp -o /usr/local/bin/yt-dlp && chmod a+rx /usr/local/bin/yt-dlp
```
