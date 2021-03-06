# node-icu-wordsplit

First, install libicu from source (so you have all the needed headers and binaries)

```sh
wget http://download.icu-project.org/files/icu4c/50.1/icu4c-50_1-src.tgz
tar -xvzf icu4c-50_1-src.tgz

cd icu/source
./configure
make
make install # or sudo make install

ldconfig # refresh linker cache
```

This will take a while. After it finishes you should have all the required ICU
headers and binaries in your default build path ready to be used.

Afterwards, switch to your project folder and

    npm install icu-wordsplit

And you should now be able to `require('icu-wordsplit')` in your code.

## API

Right now the only function call available is exported from the module.

#### splitWords ( [locale], string )

Splits the specified string into words using ICU-defined word boundary.

    var splitWords = require('icu-wordsplit');

    var results = splitWords('The quick brown fox jumps over the lazy dog.');
    console.log(results);

    results = splitWords('th_TH', 'แยกคำภาษาไทยก็ทำได้นะจ้ะ');
    console.log(results);

The first argument is the locale. You *must* specify an ICU-compatible locale name here.
However, this argument is now optional as you can use `en_US` to split most
strings without problem.

The second argument is the string to which to split.

The function will returns an array of words. Whitespaces and some common punctuations
may be automatically removed from the list.

## LICENSE

BSD

## TODO / CONTRIBUTE

All contributions welcome!

Compile and run tests with

```sh
make test
```

Here's something to do:

* More tests with more languages.
* Add more ICU functionality (like locale auto-detection.)
* Fix gyp and C++ build problems once and for all.

