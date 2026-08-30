# Translate the language of text within a request

Translate character vectors via the Google Translate API.

## Usage

``` r
gl_translate(
  t_string,
  target = "en",
  format = c("text", "html"),
  source = "",
  model = c("nmt", "base")
)
```

## Arguments

- t_string:

  Character vector of text to translate

- target:

  The target language code

- format:

  Whether the text is plain text or HTML

- source:

  Specify the language to translate from. Will detect it if left default

- model:

  Translation model to use

## Value

A tibble of `translatedText`, `detectedSourceLanguage`, and `text` of
length equal to the vector of text you passed in

## Details

You can translate a vector of strings; if too many for one call, it will
be broken up into multiple API calls with smart batching. The API
charges per character translated, so splitting does not change cost but
may take longer.

If translating HTML, set `format = "html"`. Consider removing anything
not needed to be translated first, such as JavaScript or CSS.

API limits: characters per day, characters per 100 seconds, and API
requests per 100 seconds. These can be configured in the API manager:
<https://console.developers.google.com/apis/api/translate.googleapis.com/quotas>

## See also

<https://cloud.google.com/translate/docs/reference/translate>

Other translations:
[`gl_translate_detect()`](https://docs.ropensci.org/googleLanguageR/reference/gl_translate_detect.md),
[`gl_translate_document()`](https://docs.ropensci.org/googleLanguageR/reference/gl_translate_document.md),
[`gl_translate_languages()`](https://docs.ropensci.org/googleLanguageR/reference/gl_translate_languages.md)
