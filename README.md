# Ubuntu
- http://localhost:8080/ にアクセス

# Voice
ひとまず `VOICEBOX` 使用 (Docker Hub にイメージがあったので。。)

```
cd voice
echo -n "こんにちは、音声合成の世界へようこそ" >text.txt
curl -s \
    -X POST \
    "127.0.0.1:50021/audio_query?speaker=1"\
    --get --data-urlencode text@text.txt \
    > query.json
curl -s \
    -H "Content-Type: application/json" \
    -X POST \
    -d @query.json \
    "127.0.0.1:50021/synthesis?speaker=1" \
    > audio.wav
```
TODO: プリセット用意して速さなどの設定をする
