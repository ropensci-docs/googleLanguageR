# Detect the language of text within a request

Detect the language of text within a request

## Usage

``` r
gl_translate_detect(string)
```

## Arguments

- string:

  Character vector of text to detect language for

## Value

A tibble of the detected languages with columns `confidence`,
`isReliable`, `language`, and `text`, of length equal to the vector of
text you passed in.

## Details

Consider using [`library(cld2)`](https://docs.ropensci.org/cld2/) and
[`cld2::detect_language`](https://docs.ropensci.org/cld2/reference/cld2.html)
instead for offline detection, since that is free and does not require
an API call.

[gl_translate](https://docs.ropensci.org/googleLanguageR/reference/gl_translate.md)
also returns a detection of the language, so you could optionally use
that in one step.

## See also

<https://cloud.google.com/translate/docs/reference/detect>

Other translations:
[`gl_translate()`](https://docs.ropensci.org/googleLanguageR/reference/gl_translate.md),
[`gl_translate_document()`](https://docs.ropensci.org/googleLanguageR/reference/gl_translate_document.md),
[`gl_translate_languages()`](https://docs.ropensci.org/googleLanguageR/reference/gl_translate_languages.md)

## Examples

``` r
if (FALSE) { # \dontrun{
gl_translate_detect("katten sidder på måtten")
} # }
```
