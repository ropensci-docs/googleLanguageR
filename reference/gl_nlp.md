# Perform Natural Language Analysis

Analyse text for entities, sentiment, syntax and classification using
the Google Natural Language API.

## Usage

``` r
gl_nlp(
  string,
  nlp_type = c("annotateText", "analyzeEntities", "analyzeSentiment", "analyzeSyntax",
    "analyzeEntitySentiment", "classifyText"),
  type = c("PLAIN_TEXT", "HTML"),
  language = c("en", "zh", "zh-Hant", "fr", "de", "it", "ja", "ko", "pt", "es"),
  encodingType = c("UTF8", "UTF16", "UTF32", "NONE")
)
```

## Arguments

- string:

  Character vector. Text to analyse or Google Cloud Storage URI(s) in
  the form `gs://bucket_name/object_name`.

- nlp_type:

  Character. Type of analysis to perform. Default `annotateText`
  performs all features in a single call. Options include:
  `analyzeEntities`, `analyzeSentiment`, `analyzeSyntax`,
  `analyzeEntitySentiment`, `classifyText`.

- type:

  Character. Whether the input is plain text (`PLAIN_TEXT`) or HTML
  (`HTML`).

- language:

  Character. Language of the source text. Must be supported by the API.

- encodingType:

  Character. Text encoding used to process the output. Default `UTF8`.

## Value

A list containing the requested components as specified by `nlp_type`:

- sentences:

  Sentences in the input document. [API
  reference.](https://cloud.google.com/natural-language/docs/reference/rest/v1/Sentence)

- tokens:

  Tokens with syntactic information. [API
  reference.](https://cloud.google.com/natural-language/docs/reference/rest/v1/Token)

- entities:

  Entities with semantic information. [API
  reference.](https://cloud.google.com/natural-language/docs/reference/rest/v1/Entity)

- documentSentiment:

  Overall sentiment of the document. [API
  reference.](https://cloud.google.com/natural-language/docs/reference/rest/v1/Sentiment)

- classifyText:

  Document classification. [API
  reference.](https://cloud.google.com/natural-language/docs/classifying-text)

- language:

  Detected language of the text, or the language specified in the
  request.

- text:

  Original text passed to the API. Returns `NA` if input is empty.

## Details

Encoding type can usually be left at the default `UTF8`. [Further
details on encoding
types.](https://cloud.google.com/natural-language/docs/reference/rest/v1/EncodingType)

Current language support is listed
[here](https://cloud.google.com/natural-language/docs/languages).

## See also

<https://cloud.google.com/natural-language/docs/reference/rest/v1/documents>

## Examples

``` r
if (FALSE) { # \dontrun{
library(googleLanguageR)

text <- "To administer medicine to animals is frequently difficult, yet sometimes necessary."
nlp <- gl_nlp(text)

nlp$sentences
nlp$tokens
nlp$entities
nlp$documentSentiment

# Vectorised input
texts <- c("The cat sat on the mat.", "Oh no, it did not, you fool!")
nlp_results <- gl_nlp(texts)
} # }
```
