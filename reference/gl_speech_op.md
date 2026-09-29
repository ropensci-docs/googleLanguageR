# Get a speech operation

For asynchronous calls of audio over 60 seconds, this returns the
finished job

## Usage

``` r
gl_speech_op(operation = .Last.value)
```

## Arguments

- operation:

  A speech operation object from
  [gl_speech](https://docs.ropensci.org/googleLanguageR/reference/gl_speech.md)
  when `asynch = TRUE`

## Value

If the operation is still running, another operation object. If done,
the result as per
[gl_speech](https://docs.ropensci.org/googleLanguageR/reference/gl_speech.md)

## See also

[gl_speech](https://docs.ropensci.org/googleLanguageR/reference/gl_speech.md)

## Examples

``` r

if (FALSE) { # \dontrun{

test_audio <- system.file("woman1_wb.wav", package = "googleLanguageR")

## make an asynchronous API request (mandatory for sound files over 60 seconds)
asynch <- gl_speech(test_audio, asynch = TRUE)

## Send to gl_speech_op() for status or finished result
gl_speech_op(asynch)

} # }
```
