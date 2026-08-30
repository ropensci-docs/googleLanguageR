# Authenticate with Google Language API services

Authenticate with Google Language API services

## Usage

``` r
gl_auth(json_file)

gl_auto_auth(...)
```

## Arguments

- json_file:

  Character. Path to the JSON authentication file downloaded from your
  Google Cloud project.

- ...:

  Additional arguments passed to `gar_attach_auto_auth`.

## Details

This function authenticates with Google Cloud's language APIs. By
default, it uses the JSON file specified in `json_file`. Alternatively,
you can set the file path in the environment variable `GL_AUTH` to
auto-authenticate when loading the package.

## Examples

``` r
if (FALSE) { # \dontrun{
library(googleLanguageR)
gl_auth("path/to/json_file.json")
} # }
if (FALSE) { # \dontrun{
library(googleLanguageR)
gl_auto_auth()
gl_auto_auth(environment_var = "GAR_AUTH_FILE")
} # }
```
