# Perform text to speech

Synthesizes speech synchronously: receive results after all text input
has been processed.

## Usage

``` r
gl_talk(
  input,
  output = "output.wav",
  languageCode = "en",
  gender = c("SSML_VOICE_GENDER_UNSPECIFIED", "MALE", "FEMALE", "NEUTRAL"),
  name = NULL,
  audioEncoding = c("LINEAR16", "MP3", "OGG_OPUS"),
  speakingRate = 1,
  pitch = 0,
  volumeGainDb = 0,
  sampleRateHertz = NULL,
  inputType = c("text", "ssml"),
  effectsProfileIds = NULL,
  forceLanguageCode = FALSE
)
```

## Arguments

- input:

  The text to turn into speech

- output:

  Where to save the speech audio file

- languageCode:

  The language of the voice as a `BCP-47` language code

- gender:

  The gender of the voice, if available

- name:

  Name of the voice, see list via
  [gl_talk_languages](https://docs.ropensci.org/googleLanguageR/reference/gl_talk_languages.md)
  for supported voices. Set to `NULL` to make the service choose a voice
  based on `languageCode` and `gender`.

- audioEncoding:

  Format of the requested audio stream

- speakingRate:

  Speaking rate/speed between `0.25` and `4.0`

- pitch:

  Speaking pitch between `-20.0` and `20.0` in semitones.

- volumeGainDb:

  Volumne gain in dB

- sampleRateHertz:

  Sample rate for returned audio

- inputType:

  Choose between `text` (the default) or SSML markup. The `input` text
  must be SSML markup if you choose `ssml`

- effectsProfileIds:

  Optional. An identifier which selects 'audio effects' profiles that
  are applied on (post synthesized) text to speech. Effects are applied
  on top of each other in the order they are given

- forceLanguageCode:

  If `name` is provided, this will ensure that the passed `languageCode`
  is used instead of being inferred from name. This is necessary for
  models that require the exact code (en-us, en-gb, ...), not just the
  two letters shorthand (en, es, ...)

## Value

The file output name you supplied as `output`

## Details

Requires the Cloud Text-To-Speech API to be activated for your Google
Cloud project.

Supported voices are here
<https://cloud.google.com/text-to-speech/docs/voices> and can be
imported into R via
[gl_talk_languages](https://docs.ropensci.org/googleLanguageR/reference/gl_talk_languages.md)

To play the audio in code via a browser see
[gl_talk_player](https://docs.ropensci.org/googleLanguageR/reference/gl_talk_player.md)

To use Speech Synthesis Markup Language (SSML) select `inputType=ssml` -
more details on using this to insert pauses, sounds and breaks in your
audio can be found here:
<https://cloud.google.com/text-to-speech/docs/ssml>

To use audio profiles, supply a character vector of the available audio
profiles listed here:
<https://cloud.google.com/text-to-speech/docs/audio-profiles> - the
audio profiles are applied in the order given. For instance
`effectsProfileIds="wearable-class-device"` will optimise output for
smart watches,
`effectsProfileIds=c("wearable-class-device","telephony-class-application")`
will apply sound filters optimised for smart watches, then telephonic
devices.

## See also

<https://cloud.google.com/text-to-speech/docs/>

## Examples

``` r

if (FALSE) { # \dontrun{
library(magrittr)
gl_talk("The rain in spain falls mainly in the plain",
        output = "output.wav")

gl_talk("Testing my new audio player") %>% gl_talk_player()

# using SSML
gl_talk('<speak>The <say-as interpret-as=\"characters\">SSML</say-as>
  standard <break time=\"1s\"/>is defined by the
  <sub alias=\"World Wide Web Consortium\">W3C</sub>.</speak>',
  inputType =  "ssml")

# using effects profiles
gl_talk("This sounds great on headphones",
        effectsProfileIds = "headphone-class-device")

} # }
```
