# **privnote-cli** [![Build Status](https://secure.travis-ci.org/nonrational/privnote-cli.svg?branch=master)](http://travis-ci.org/nonrational/privnote-cli)
_the power of [privnote.com](https://privnote.com) in your terminal_

#### [privnote.com](https://privnote.com): Send notes that will self-destruct after being read.

Privnote allows you to create and share encrypted, burn-after-reading notes over the internet. It's a great way to share passwords or other sensitive peices of information. But, you have to use a web browser! Or, should I say, _had_ to.

### Installation

```bash
npm install -g privnote-cli
# don't forget to `nodenv rehash` if you're using nodenv
```

### Usage

You bring the plaintext; `privnote` will print the link to stdout _and_ the clipboard.

#### Type directly into stdin a la `gpg`. (Recommended)

```
$ privnote
bob,
the narwhal bacons at midnight.
-- alice
^D
https://privnote.com/n/abcdefghijklmnop/#qrstuvwxyz123456
```

#### Pipe the output of a command to privnote.

Be sure to clear your shell history (`$HISTFILE`) if you included secrets in your command.

```
$ ruby -e 'require "securerandom"; print "#{SecureRandom.urlsafe_base64(12)}\n";' | privnote
https://privnote.com/n/abcdefghijklmnop/#qrstuvwxyz123456
```

#### Privnote files directly via input redirection.

```
$ privnote < secrets.txt
https://privnote.com/n/abcdefghijklmnop/#qrstuvwxyz123456
```

#### Release History

- v0.2.1 - Fix `yarn` installation (h/t @deecewan)
- v0.2.0 - Default to "no-ask" mode & provide --ask flag, upgrade to Privnote Ver. 1.1-24-gffcdb2d
- v0.1.0 - more recent node, remove trailing space, specify license
- v0.0.12 - Fixed compatibility with Privnote Ver. 1.0-41-g038c13a

##### Releasing

```
echo "doh! i forgot the releasing section" >> README.md
git add --all
git commit -m"added the releasing section, bc i'm forgetful."
npm version patch
git push origin master
npm publish
```
