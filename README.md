# mutt-gmail-patches
Updates of patches to mutt to support Gmail features

The current version of the patch will enable GMail IMAP extensions and the following features
* `X-Gm-Msgid` message header
* `X-Gm-Permalink` message header
* The GMail labels via `%y` in index_format

*Note:* You may need to clear/delete your header cache once you've applied the patch

## How to apply these patches

1. Download the version of mutt you are interested in using from [mutt.org](http://www.mutt.org/)
2. Download the patch that matches the version of mutt you are using
3. Untar the source code for mutt
4. cd into the mutt folder
5. apply the patch

## Example

You can use the following commands to patch the latest version of mutt:

```
% wget ftp://ftp.mutt.org/pub/mutt/mutt-2.0.3.tar.gz
% wget https://raw.githubusercontent.com/kuperman/mutt-gmail-patches/master/patch-2.0.3.bk.gmail-labels.1
% tar xzvf mutt-2.0.3.tar.gz
% cd mutt-2.0.3
% patch -p1 < ../patch-2.0.3.bk.gmail-labels.1
```

## Working with Homebrew

I need to update my tap of mutt to support this patch. However, for now you can just build this on your own using the same options as Homebrew used.

1. Edit the recipie via `brew edit mutt`
2. Add in the following lines
```
patch do
    url "https://raw.githubusercontent.com/kuperman/mutt-gmail-patches/master/patch-2.0.3.bk.gmail-labels.1"
    sha256 "83416ee11f0b532517b71f76a21da96f6ae2cc316b64465fee0db936f39d8c18"
end
```
3. Build from source `brew reinstall --build-from-source mutt`

For previous versions you can include the following:  
**mutt-1.13.2**
```
patch do
    url "https://raw.githubusercontent.com/kuperman/mutt-gmail-patches/master/patch-1.13.2.bk.gmail-labels.1"
    sha256 "8e5504fe2a3e89ca45cafea8cc3d4fc7ee1415ff64aa6ebb6c9164797ac7ec9d"
end
```
**mutt-1.12.2**
```
patch do
    url "https://raw.githubusercontent.com/kuperman/mutt-gmail-patches/master/patch-1.12.2.bk.gmail-labels.1"
    sha256 "2470d0101fe78c1c01d2b17c6f4c25375a7664f7b14d115f813f93647c9c06de"
end
```
**mutt-1.11.1**
```
patch do
    url "https://raw.githubusercontent.com/kuperman/mutt-gmail-patches/master/patch-1.11.1.bk.gmail-labels.1"
    sha256 "55988e5e78f2af64769117dc1da94acbddb47766b7c2b6c9f543d63940086c8e"
end
```

### References
The original version of these patches are from https://github.com/sgeb/homebrew-mutt/tree/master/patches

## Gmail server side custom search patch

Conflicts with Gmail label patch above


```
patch do
    url "https://raw.githubusercontent.com/kuperman/mutt-gmail-patches/master/patch-2.0.3.bk.gmail-customsearch.1"
    sha256 "4d9c0a64c975693fcb87bd13f48cb8ecac300e687079025be77f73c80f375ca5"
end
```

Originally from [Phil Pennock](https://marc.info/?l=mutt-dev&m=131219876908901)
via the [mutt-dev](http://www.mutt.org/mail-lists.html) mailing list and
earlier ports of this in patch files.

## Patch that combines search and labels

```
patch do
    url "https://raw.githubusercontent.com/kuperman/mutt-gmail-patches/master/patch-2.0.3.bk.gmail-extensions.1"
    sha256 "086fa9039b0a74d61b50bdd64a450d1f6f080130e60d6b6ab97a7183480c350b"
end
```
