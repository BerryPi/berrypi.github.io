# Magical Mirai Programming Contest 2023
The aim of [this contest](https://magicalmirai.com/2023/procon/index_en.html) was to make an application with the [TextAlive API](https://developer.textalive.jp/events/magicalmirai2023/) to display a song's lyrics in time with the music.

This was my first time using [TextAlive](textalive), and implementing most of it with [CSS Animations](css_animation) meant I had to solve some new problems with those.

The finished product is [here](https://berrypi.github.io/MagicalMiraiProgramming2023/), and the source [here](https://github.com/BerryPi/MagicalMiraiProgramming2023).

(yes all the CSS and JavaScript are in the same file. because of CORS, loading the JS from a separate file would have required spinning up a web server which is marginally more effort than just opening the HTML file)

(at one point i went so far as to base64 the images just so that the whole thing could be a single file, but that would have been *too* silly to commit.)