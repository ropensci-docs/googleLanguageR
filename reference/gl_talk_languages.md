# Get a list of voices available for text to speech

Returns a list of voices supported for synthesis.

## Usage

``` r
gl_talk_languages(languageCode = NULL)
```

## Arguments

- languageCode:

  A `BCP-47` language tag. If specified, will only return voices that
  can be used to synthesize this languageCode
