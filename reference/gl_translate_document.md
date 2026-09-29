# Translate a document via the Google Translate API

Translate a document via the Google Translate API

## Usage

``` r
gl_translate_document(
  d_path,
  target = "es-ES",
  output_path = "out.pdf",
  format = c("pdf"),
  source = "en-UK",
  model = c("nmt", "base"),
  location = "global"
)
```

## Arguments

- d_path:

  Path to the document to be translated

- target:

  Target language code (default "es-ES")

- output_path:

  Path where to save the translated document (default "out.pdf")

- format:

  Document format. Currently, only "pdf" is supported

- source:

  Source language code (default "en-UK")

- model:

  Translation model to use ("nmt" or "base")

- location:

  Location for translation API (default "global")

## Value

The full path of the translated document

## See also

Other translations:
[`gl_translate()`](https://docs.ropensci.org/googleLanguageR/reference/gl_translate.md),
[`gl_translate_detect()`](https://docs.ropensci.org/googleLanguageR/reference/gl_translate_detect.md),
[`gl_translate_languages()`](https://docs.ropensci.org/googleLanguageR/reference/gl_translate_languages.md)

## Examples

``` r
if (FALSE) { # \dontrun{
gl_translate_document(
  system.file(package = "googleLanguageR", "test-doc.pdf"),
  target = "no"
)
} # }
```
