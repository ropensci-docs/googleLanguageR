# Speak in Shiny module (server)

Call via `shiny::callModule(gl_talk_shiny, "your_id")`

## Usage

``` r
gl_talk_shiny(
  input,
  output,
  session,
  transcript,
  ...,
  autoplay = TRUE,
  controls = TRUE,
  loop = FALSE,
  keep_wav = FALSE
)
```

## Arguments

- input:

  shiny input

- output:

  shiny output

- session:

  shiny session

- transcript:

  The (reactive) text to talk

- ...:

  Arguments passed on to
  [`gl_talk`](https://docs.ropensci.org/googleLanguageR/reference/gl_talk.md)

  `languageCode`

  :   The language of the voice as a `BCP-47` language code

  `name`

  :   Name of the voice, see list via
      [gl_talk_languages](https://docs.ropensci.org/googleLanguageR/reference/gl_talk_languages.md)
      for supported voices. Set to `NULL` to make the service choose a
      voice based on `languageCode` and `gender`.

  `gender`

  :   The gender of the voice, if available

  `audioEncoding`

  :   Format of the requested audio stream

  `speakingRate`

  :   Speaking rate/speed between `0.25` and `4.0`

  `pitch`

  :   Speaking pitch between `-20.0` and `20.0` in semitones.

  `volumeGainDb`

  :   Volumne gain in dB

  `sampleRateHertz`

  :   Sample rate for returned audio

  `inputType`

  :   Choose between `text` (the default) or SSML markup. The `input`
      text must be SSML markup if you choose `ssml`

  `effectsProfileIds`

  :   Optional. An identifier which selects 'audio effects' profiles
      that are applied on (post synthesized) text to speech. Effects are
      applied on top of each other in the order they are given

  `forceLanguageCode`

  :   If `name` is provided, this will ensure that the passed
      `languageCode` is used instead of being inferred from name. This
      is necessary for models that require the exact code (en-us, en-gb,
      ...), not just the two letters shorthand (en, es, ...)

- autoplay:

  passed to the HTML audio player - default `TRUE` plays on load

- controls:

  passed to the HTML audio player - default `TRUE` shows controls

- loop:

  passed to the HTML audio player - default `FALSE` does not loop

- keep_wav:

  keep the generated wav files if TRUE.
