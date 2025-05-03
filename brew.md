You can install homebrew anywhere. You are not limited to the default `/opt/homebrew` which requires Administrator permissions during install. It is very unsupported, however, and they make that very clear on their site. Despite that, I have had very minimal issues. Give it a shot. It's simple, just follow the docs

https://docs.brew.sh/Installation#untar-anywhere-unsupported



A "tap" is a repo
You can add a "tap" to get access to private formulae

You can export all the packages that you have explicitly installed with
`brew bundle dump` which dumps it out to [Brewfile](Brewfile)
