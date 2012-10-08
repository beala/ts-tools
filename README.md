A collection of bash scripts for working with [secure timestamps](http://en.wikipedia.org/wiki/Trusted_timestamping).

## tsr

`tsr` securely timestamps a file.

For example:

```
tsr -f my_file.txt -s http://tsa.starfieldtech.com
```

This will result in two files:  `my_file.tsr` and `my_file.tsq`. The `tsr` file is the
timestamp file (a 'timestamp reply').

## tsv

`tsv` verifies a timestamp.

For example:

```
tsv -r my_file.tsr -f my_file.txt -s CA_cert.crt
```

Where `CA_cert.crt` is the signing certificate of the CA that signed the 
timestamp. This can usually be found by googling. Star Field Tech's certificate
is here: [https://certs.starfieldtech.com/anonymous/repository.seam](https://certs.starfieldtech.com/anonymous/repository.seam)

## Config

Be sure to set the `$OPEN_SSL` path at the top of both `tsr` and `tsv`. The version it is
pointing to must be >= v0.9.9. On OS X, this can be installed with `homebrew`.

```
brew install openssl
```

If the correct version is already in your `$PATH`, just set it to `openssl`.

## License

```
Copyright (c) 2012 Alex Beal <alexlbeal@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
