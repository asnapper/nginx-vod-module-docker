# HLS & DASH example

## Running this example locally

You can run this example locally with Docker

```
% docker run -p 3030:80 -v $PWD/videos:/opt/static/videos -v $PWD/nginx.conf:/usr/local/nginx/conf/nginx.conf asnapper/nginx-vod-module:with-secure-token
```

After running this command, you should be able to play the following URLs:

- HLS (with encrypted URL): http://localhost:3030/hls/_Jt6EDpqR4ZJdEKgpJOoQYiXflVRKh5UaoVl7S01x4G-r1biX6p0WarMqihUyg56xVVOfsYUx4xPVLG8aUMtdAr5JGxMSC7PMd4Ds6gYldY
- Dash: http://localhost:3030/dash/devito,360p.mp4,480p.mp4,720p.mp4,.en_US.vtt,.urlset/manifest.mpd
- Thumbnail: http://localhost:3030/thumb/devito360p.mp4/thumb-1000.jpg

Encrypted URL for HLS has been generated using encryptUrl.py from kaltura nginx secure token module using the following command (on bash):
```
echo "http://localhost:3030$(python encryptUrl.py /hls/ devito,360p.mp4,480p.mp4,720p.mp4,.en_US.vtt,.urlset/master.m3u8 000102030405060708090a0b0c0d0e0f101112131415161718191a1b1c1d1e1f 00000000000000000000000000000000)"
```