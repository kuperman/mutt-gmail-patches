# mutt-gmail-patches
Updates of patches to mutt to support Gmail features

## How to apply these patches

1. Download the version of mutt you are interested in using from [mutt.org](http://www.mutt.org/)
2. Download the patch that matches the version of mutt you are using
3. Untar the source code for mutt
4. cd into the mutt folder
5. apply the patch

## Example

You can use the following commands to patch the latest version of mutt:

```
% wget ftp://ftp.mutt.org/pub/mutt/mutt-1.11.1.tar.gz
% wget https://raw.githubusercontent.com/kuperman/mutt-gmail-patches/master/patch-1.11.1.bk.gmail-labels.1
% tar xzvf mutt-1.11.1.tar.gz
% cd mutt-1.11.1
% patch -p1 < ../patch-1.11.1.bk.gmail-labels.1
```

## Working with Homebrew

I need to update my tap of mutt to support this patch. However, for now you can just build this on your own using the same options as Homebrew used.

1. Edit the recipie via `brew edit mutt`
2. Add in the following lines
```
patch do
    url "https://raw.githubusercontent.com/kuperman/mutt-gmail-patches/master/patch-1.11.1.bk.gmail-labels.1"
    sha256 "55988e5e78f2af64769117dc1da94acbddb47766b7c2b6c9f543d63940086c8e"
end
```
3. Build from source `brew reinstall --build-from-source mutt`

<!--
1. Install mutt via homebrew `brew install mutt`
2. Get the config options via `mutt -v | grep Configure`
3. Follow the steps above to get the patch applied
4. Build using `./configure` with all of the options listed in the output from above (e.g., `./configure '--disable-dependency-tracking' '--disable-warnings' '--prefix=/usr/local/Cellar/mutt/1.11.1_1' '--enable-debug' '--enable-hcache' '--enable-imap' '--enable-pop' '--enable-sidebar' '--enable-smtp' '--with-gss' '--with-sasl' '--with-ssl=/usr/local/opt/openssl' '--with-tokyocabinet' 'CC=clang'` )
5. Run `make`
6. Copy the binary into the usual location `cp -f ./mutt /usr/local/bin/mutt` (The '-f' is needed because the write bit is off in homebrew installations).
-->

### References
The original version of these patches are from https://github.com/sgeb/homebrew-mutt/tree/master/patches
