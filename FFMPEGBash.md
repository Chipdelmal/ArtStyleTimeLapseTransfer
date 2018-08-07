# FFMpeg Bash Commands

## Get all the frames and export a MPEG

ffmpeg -start_number 1 -r 5 -f image2 -s 720x540 -i %04d.png -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" -vcodec libx264 -preset veryslow -crf 15 -pix_fmt yuv420p ArtStyleML.mp4


## Generate GIF color palette

ffmpeg -i ArtStyleML.mp4 -i palette.png -r 15 -lavfi paletteuse image.gif

## Use palette to generate the GIF

ffmpeg -ss 2.6 -i ArtStyleML.mp4 -i palette.png \-filter_complex "fps=5,scale=500:-1:flags=lanczos[x];[x][1:v]paletteuse" sixthtry.gif
