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

Additional tweaks needed:

`<<setPrivacy defaultValue:private>>`
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
  - [x] Reproduce empty.html from MPTW https://github.com/simonbaird/MPTW/
 - [x] Unevaluated macro code in tiddlers created via [NewButtons](tiddlers/NewButtons.tiddler)
   - Add `config.evaluateMacroParameters = "full";` 
 - [x] Broken plugins (MptwConfigPlugin, QuickOpenTagPlugin, TagglyTaggingPlugin)
    - Needed to extend hackery in build.rb to 2.8.x
 - [x] initial.html (for importing)
 - [x] DefaultTiddlers: GettingStarted
   - Delete forbidden (even though in my public bag?)
   - Fixed by adding DefaultTiddlers to initial.html
 - [x] why is default privacy sometimes public?
   - In one space, SystemSettings had options.chkPrivacyMode = false
     
## Still broken

- [x] why is refresh sometimes broken?
  - Seems to happen when JS errors arise. Keep an eye out and fix them as they come up.
- [ ] Changing states using mGSD UI doesn't trigger autosave
  - setTiddlerTag doesn't trigger autosave. I think this is by design.
  - need to call autoSave on each UI action
  - [ ] toggleTag macro
    
- [ ] Add zzMgsdConfig to initial.html

## Release tasks

- [ ] Stabilize mgsd space and switch development to mgsd-head
- [ ] Host initial.html somewhere and add instructions (maybe upload as binary file to another space?)
- [ ] Make it really easy to create a new mGSD in tiddlyspace
