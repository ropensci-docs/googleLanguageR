# Lists languages from Google Translate API

Returns a list of supported languages for translation.

## Usage

``` r
gl_translate_languages(target = "en")
```

## Arguments

- target:

  A language code for localized language names (default 'en')

## Value

A tibble of supported languages

## Details

Supported language codes generally consist of their ISO 639-1
identifiers (e.g., `'en', 'ja'`). In certain cases, BCP-47 codes
including language + region identifiers are returned (e.g.,
`'zh-TW', 'zh-CH'`).

## See also

<https://cloud.google.com/translate/docs/reference/languages>

Other translations:
[`gl_translate()`](https://docs.ropensci.org/googleLanguageR/reference/gl_translate.md),
[`gl_translate_detect()`](https://docs.ropensci.org/googleLanguageR/reference/gl_translate_detect.md),
[`gl_translate_document()`](https://docs.ropensci.org/googleLanguageR/reference/gl_translate_document.md)

## Examples

``` r
if (FALSE) { # \dontrun{
gl_translate_languages()
gl_translate_languages("da")
} # }
```
