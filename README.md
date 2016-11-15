# elm-md5

Compute MD5 message digests in Elm.

## Quick Start

This library exposes just one function, `hex`, which takes a `String` input and returns the 128-bit MD5
digest as a `String` of 32 hexadecimal characters.

```elm
MD5.hex ""          == "d41d8cd98f00b204e9800998ecf8427e"
MD5.hex "foobarbaz" == "6df23dc03f9b54cc38a0fc1483df6e21"
```

Unlike the [JavaScript program](https://css-tricks.com/snippets/javascript/javascript-md5/) upon which this
implementation is based, CRLF pairs in the input are not automatically replaced with LFs prior to computing
the digest. If you want that behaviour, adjust the input before evaluating the function. For example:

```elm
myHex : String -> String
myHex input =
    let
        myInput =
            Regex.replace Regex.All (Regex.regex "\x0D\n") (\_ -> "\n") input
    in
        MD5.hex myInput
```

# Versioning

In the dependencies section of `elm-package.json` use the following. For Elm 0.17:

```json
"sanichi/md5": "1.0.0 <= v < 1.0.1"
```

For Elm 0.18:

```json
"sanichi/md5": "1.0.1 <= v < 2.0.0"
```

I would rather have bumped the version to 2.0.0 for the Elm 0.18 upgrade but the package publishing tools
prevented this since the API had not changed.
