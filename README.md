# Presentation with markdown and pandoc

## How to use
Execute the following command. Everytime the presentation.md file is saved, pandoc is beeing executed.
```bash
ag -l | entr -s \
"pandoc --slide-level 1 --lua-filter dotfilter.lua \
 presentation.md -t beamer -o presentation.pdf"
```

## Needed Tools
* pandoc
* ag 
* entr
