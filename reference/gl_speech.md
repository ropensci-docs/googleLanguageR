# Call Google Speech API

Turn audio into text

## Usage

``` r
gl_speech(
  audio_source,
  encoding = c("LINEAR16", "FLAC", "MULAW", "AMR", "AMR_WB", "OGG_OPUS",
    "SPEEX_WITH_HEADER_BYTE"),
  sampleRateHertz = NULL,
  languageCode = "en-US",
  maxAlternatives = 1L,
  profanityFilter = FALSE,
  speechContexts = NULL,
  asynch = FALSE,
  customConfig = NULL
)
```

## Arguments

- audio_source:

  File location of audio data, or Google Cloud Storage URI

- encoding:

  Encoding of audio data sent

- sampleRateHertz:

  Sample rate in Hertz of audio data. Valid values `8000-48000`. Optimal
  and default if left `NULL` is `16000`

- languageCode:

  Language of the supplied audio as a `BCP-47` language tag

- maxAlternatives:

  Maximum number of recognition hypotheses to be returned. `0-30`

- profanityFilter:

  If `TRUE` will attempt to filter out profanities

- speechContexts:

  An optional character vector of context to assist the speech
  recognition

- asynch:

  If your `audio_source` is greater than 60 seconds, set this to TRUE to
  return an asynchronous call

- customConfig:

  \[optional\] A `RecognitionConfig` object that will be converted from
  a list to JSON via
  [`toJSON`](https://jeroen.r-universe.dev/jsonlite/reference/fromJSON.html) -
  see [RecognitionConfig
  documentation](https://cloud.google.com/speech-to-text/docs/reference/rest/v1p1beta1/RecognitionConfig).
  The `languageCode` will be taken from this functions arguments if not
  present since it is required.

## Value

A list of two tibbles: `$transcript`, a tibble of the `transcript` with
a `confidence`; `$timings`, a tibble that contains `startTime`,
`endTime` per `word`. If maxAlternatives is greater than 1, then the
transcript will return near-duplicate rows with other interpretations of
the text. If `asynch` is TRUE, then an operation you will need to pass
to
[gl_speech_op](https://docs.ropensci.org/googleLanguageR/reference/gl_speech_op.md)
to get the finished result.

## Details

Google Cloud Speech API enables developers to convert audio to text by
applying powerful neural network models in an easy to use API. The API
recognizes over 80 languages and variants, to support your global user
base. You can transcribe the text of users dictating to an application’s
microphone, enable command-and-control through voice, or transcribe
audio files, among many other use cases. Recognize audio uploaded in the
request, and integrate with your audio storage on Google Cloud Storage,
by using the same technology Google uses to power its own products.

## AudioEncoding

Audio encoding of the data sent in the audio message. All encodings
support only 1 channel (mono) audio. Only FLAC and WAV include a header
that describes the bytes of audio that follow the header. The other
encodings are raw audio bytes with no header. For best results, the
audio source should be captured and transmitted using a lossless
encoding (FLAC or LINEAR16). Recognition accuracy may be reduced if
lossy codecs, which include the other codecs listed in this section, are
used to capture or transmit the audio, particularly if background noise
is present.

Read more on audio encodings here
<https://cloud.google.com/speech-to-text/docs/encoding>

## WordInfo

`startTime` - Time offset relative to the beginning of the audio, and
corresponding to the start of the spoken word.

`endTime` - Time offset relative to the beginning of the audio, and
corresponding to the end of the spoken word.

`word` - The word corresponding to this set of information.

## See also

<https://cloud.google.com/speech/reference/rest/v1/speech/recognize>

## Examples

``` r

if (FALSE) { # \dontrun{

test_audio <- system.file("woman1_wb.wav", package = "googleLanguageR")
result <- gl_speech(test_audio)

result$transcript
result$timings

result2 <- gl_speech(test_audio, maxAlternatives = 2L)
result2$transcript

result_brit <- gl_speech(test_audio, languageCode = "en-GB")


## make an asynchronous API request (mandatory for sound files over 60 seconds)
asynch <- gl_speech(test_audio, asynch = TRUE)

## Send to gl_speech_op() for status or finished result
gl_speech_op(asynch)

## Upload to GCS bucket for long files > 60 seconds
test_gcs <- "gs://mark-edmondson-public-files/googleLanguageR/a-dream-mono.wav"
gcs <- gl_speech(test_gcs, sampleRateHertz = 44100L, asynch = TRUE)
gl_speech_op(gcs)

## Use a custom configuration
my_config <- list(encoding = "LINEAR16",
                  diarizationConfig = list(
                    enableSpeakerDiarization = TRUE,
                    minSpeakerCount = 2,
                    maxSpeakCount = 3
                    ))

# languageCode is required, so will be added if not in your custom config
gl_speech(my_audio, languageCode = "en-US", customConfig = my_config)

} # }


```
