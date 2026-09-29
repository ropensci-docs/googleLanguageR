# Play audio in a browser

This uses HTML5 audio tags to play audio in your browser

## Usage

``` r
gl_talk_player(audio = "output.wav", html = "player.html")
```

## Arguments

- audio:

  The file location of the audio file. Must be supported by HTML5

- html:

  The html file location that will be created host the audio

## Details

A platform neutral way to play audio is not easy, so this uses your
browser to play it instead.

## Examples

``` r

if (FALSE) { # \dontrun{

gl_talk("Testing my new audio player") %>% gl_talk_player()

} # }
```
