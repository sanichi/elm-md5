# elm-md5

Compute MD5 message digests in Elm.

## Quick Start

This library exposes just one function (_hex_) which takes one _String_ input and returns the 128-bit MD5
digest as a _String_ of 32 hexadecimal characters.

```elm
MD5.hex ""          == "d41d8cd98f00b204e9800998ecf8427e"
MD5.hex "foobarbaz" == "6df23dc03f9b54cc38a0fc1483df6e21"
```

Unlike the [Javascript program](https://css-tricks.com/snippets/javascript/javascript-md5/) upon which this
implementation is based, CRLF pairs in the input are not automatically replaced with LFs prior to computing
the digest. If you want that behaviour you should adjust the input yourself before evaluating the function.
For example:

```elm
myHex : String -> String
myHex input =
    let
        myInput =
            Regex.replace Regex.All (Regex.regex "\x0D\n") (\_ -> "\n") input
    in
        MD5.hex myInput
```
