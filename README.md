This is [@edrex](https://twitter.com/edrex)'s fork of [mGSD](http://mgsd.tiddlyspot.com/) to make changes needed for compatibility with TiddlySpace. It is not meant as a feature fork, and ideally will be merged back into Simon's repo. It 

## Goals

 - Uploading an empty mGSD to tiddlyspace should Just Work™
 - Provide mGSD on TiddlySpace as an includable app at [mgsd.tiddlyspace.com](http://mgsd.tiddlyspace.com).
 - Longer-term, develop a data-format-compatible clone of mGSD as a [SPA](http://faq.tiddlyspace.com/SPA) or [TiddlyWiki5](http://tiddlywiki.com) app. This will work alongside the includable mGSD so I can stay productive while developing the new tool.
 
## Create your own mGSD hosted on TiddlySpace

1. Create a new space
2. Visit /\_space and:
  1. Remove all includes
  2. Add **mgsd** include.
3. Using backstage, import the contents of upload/initial.html

## Build

### Ruby

The build scripts require Ruby 1.8 and won't work with newer versions.

To build under OSX/Homebrew:

```
brew install ruby186
RUBY=/usr/local/opt/ruby186/bin/ruby
$RUBY build.rb
```

### MPTW

mGSD has a copy of the output of [MPTW]()'s build at `empties/empty.html`. If you want to update to a new version of TiddlyWiki or make changes to the MPTW parts, you'll need to rebuild MPTW.

### Let's fix mGSD on TiddlySpace

 - [x] Build with latest TiddlyWiki (2.8.1)
  - [x] `brew install ruby18` (needed for r4tw.rb)
  - [x] Reproduce empty.html from MPTW
 - [x] Unevaluated macro code in tiddlers created via [NewButtons](tiddlers/NewButtons.tiddler)
   - Needed to add `config.evaluateMacroParameters = "full";`
 - [x] Upgrade mGSD
   - [x] New empty.html
     - [x] Upgrade MPTW   
       - https://github.com/simonbaird/MPTW/
       - http://classic.tiddlywiki.com/
 - [x] Broken plugins (fix in MPTW or mGSD?)
   - MptwConfigPlugin
   - QuickOpenTagPlugin
   - TagglyTaggingPlugin

## Still so broken

- [ ] Can import initial data from tiddlyspace URL?
- [ ] New tiddlers are still saving to public bag. Why?
- [ ] Settings to ensure private save and code eval
  - [ ] Initial
  - [ ] MgtdSettings
- [ ] Stablize mgsd space and switch development to mgsd-head
- Make it really easy to create a new mGSD in tiddlyspace
  - 
