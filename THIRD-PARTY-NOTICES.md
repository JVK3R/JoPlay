# Third-party notices

JoPlay is © JVK3R, all rights reserved. It is built with the open-source work below, used under each one's licence. The full licence texts are in [licenses/](licenses).

| What | Used for | Licence | Text |
|---|---|---|---|
| [FFmpeg](https://ffmpeg.org) 7.1 | Playing video and sound | LGPL 2.1 or later | [FFmpeg-LGPL-2.1.txt](licenses/FFmpeg-LGPL-2.1.txt) |
| [libwebp](https://chromium.googlesource.com/webm/libwebp) 1.4.0 (decoder) | Posters in WebP | BSD 3-Clause, © 2010 Google Inc. | [libwebp-COPYING.txt](licenses/libwebp-COPYING.txt), [libwebp-PATENTS.txt](licenses/libwebp-PATENTS.txt) |
| [lwIP](https://savannah.nongnu.org/projects/lwip/) 2.2.1 | Networking inside the Mullvad tunnel | BSD 3-Clause, © Swedish Institute of Computer Science | [lwIP-COPYING.txt](licenses/lwIP-COPYING.txt) |
| [Mbed TLS](https://github.com/Mbed-TLS/mbedtls) 3.6.8 | Secure connections inside the Mullvad tunnel | Apache 2.0, © The Mbed TLS Contributors | [MbedTLS-LICENSE.txt](licenses/MbedTLS-LICENSE.txt) |
| [Monocypher](https://monocypher.org) 4.0.2 | WireGuard encryption | BSD 2-Clause (or CC0), © Loup Vaillant and contributors | [Monocypher-LICENCE.md](licenses/Monocypher-LICENCE.md) |
| [BLAKE2](https://github.com/BLAKE2/BLAKE2) reference code | WireGuard hashing | CC0 1.0 | [BLAKE2-COPYING.txt](licenses/BLAKE2-COPYING.txt) |
| [stb](https://github.com/nothings/stb) (stb_image, stb_image_write, stb_truetype) | Pictures and text | MIT (or public domain), © Sean Barrett | [stb-LICENSE.txt](licenses/stb-LICENSE.txt) |
| [Exo 2](https://github.com/googlefonts/Exo-2.0) | The app's font | SIL Open Font License 1.1, © The Exo 2 Project Authors | [Exo2-OFL.txt](licenses/Exo2-OFL.txt) |
| Mozilla's trusted certificate list, as [published by curl](https://curl.se/docs/caextract.html) | Checking secure connections | [Mozilla Public License 2.0](https://www.mozilla.org/MPL/2.0/) | Shipped unchanged as `assets/ca-bundle.pem`; its source is [curl.se/ca/cacert.pem](https://curl.se/ca/cacert.pem) |
| LLVM compiler-rt builtins | Low-level maths the compiler needs | Apache 2.0 with LLVM exception | [llvm.org/LICENSE.txt](https://llvm.org/LICENSE.txt) |

## FFmpeg

JoPlay contains FFmpeg 7.1, built as static LGPL libraries (libavcodec, libavformat, libavutil, libswresample, libswscale) with no GPL or non-free parts switched on. FFmpeg's source is not changed.

Every release on this page carries, next to the `.pkg`:

- `ffmpeg-7.1.tar.xz`: FFmpeg's complete source, exactly as [ffmpeg.org](https://ffmpeg.org/releases/) publishes it (SHA-256 `40973d44970dbc83ef302b0609f2e74982be2d85916dd2ee7472d30678a7abe6`).
- `joplay-objects-<version>.zip`: JoPlay's compiled object files and the link command, so you can link JoPlay against your own build of FFmpeg.

FFmpeg was configured with these settings (`$PREFIX` is where it installs, `$OO` the [OpenOrbis PS4 toolchain](https://github.com/OpenOrbis/OpenOrbis-PS4-Toolchain) v0.5.4):

```
--prefix=$PREFIX --enable-cross-compile --arch=x86_64 --target-os=freebsd --cc=clang --cxx=clang++ --host-cc=clang
--ar=llvm-ar --ranlib=llvm-ranlib --nm=llvm-nm --strip=llvm-strip
--extra-cflags='--target=x86_64-pc-freebsd12-elf -fPIC -funwind-tables -D__PS4__ -D__OPENORBIS__ -D__BSD_VISIBLE
  -D_BSD_SOURCE -isysroot $OO -isystem $OO/include'
--extra-ldflags='--target=x86_64-pc-freebsd12-elf -fuse-ld=lld -nostdlib -Wl,-m,elf_x86_64 -Wl,-pie
  -Wl,--script=$OO/link.x -Wl,--eh-frame-hdr -L$OO/lib $OO/lib/crt1.o'
--extra-libs='-lc -lkernel -lclang_rt.builtins-x86_64'
--disable-shared --enable-static --enable-pic --disable-programs --disable-doc --disable-debug --disable-autodetect
--disable-avdevice --disable-avfilter --disable-network --disable-everything --enable-protocol=file
--enable-demuxer='matroska,mov,mpegts,avi,flv,ogg,wav,mp3,aac,ac3,eac3,hls,webm_dash_manifest'
--enable-decoder='h264,hevc,mpeg4,mpeg2video,vc1,vp8,vp9,av1'
--enable-decoder='aac,aac_latm,ac3,eac3,mp3,mp2,opus,vorbis,flac,dca,truehd,mlp,alac,pcm_s16le,pcm_s24le,pcm_s32le,pcm_f32le'
--enable-decoder='subrip,ass,ssa,webvtt,mov_text,dvd_subtitle,hdmv_pgs_subtitle' --enable-decoder=webp
--enable-parser='h264,hevc,mpeg4video,mpegvideo,vc1,vp8,vp9,av1,aac,aac_latm,ac3,mpegaudio,opus,vorbis,flac,dca,mlp'
--enable-bsf='h264_mp4toannexb,hevc_mp4toannexb,aac_adtstoasc,extract_extradata'
--enable-swscale --enable-swresample --x86asmexe=nasm
```

## Open Movies

The three built-in films are by the [Blender Foundation](https://www.blender.org/about/projects/), under [Creative Commons Attribution 3.0](https://creativecommons.org/licenses/by/3.0/). They are not changed. Each one's credit is shown in JoPlay with the film.

- **Big Buck Bunny** (2008): © copyright 2008, Blender Foundation / www.bigbuckbunny.org
- **Sintel** (2010): © copyright Blender Foundation | durian.blender.org
- **Tears of Steel** (2012): (CC) Blender Foundation | mango.blender.org

## Names

Stremio, Mullvad, PlayStation and PS4 are the trademarks of their owners. JoPlay is not affiliated with or endorsed by any of them.
