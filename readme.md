# Installing Postgres via Brew

## Pre-Reqs
[Brew Package Manager](http://brew.sh)

In your command-line run the following commands:

1. `brew doctor`
1. `brew update`

## Installing
1. In your command-line run the command: `brew install postgresql`
2. Read the **Caveats** section that is outputted to the Terminal. (out dated?)
3. Run the command: `ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents`
4. Open your zsh config file: `subl ~/.zshrc`
5. At the bottom of the file, create two new aliases to start and stop your postgres server. They could look something like this:

     ```
     alias pg-start="launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist"
     alias pg-stop="launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist"
     ```

6. Run the command: `source ~/.zshrc` to reload your configuration.
7. Run the alias you just created: `pg-start`. Use this comment to start your database service.
     - alternatively, `pg-stop` stops your database service.
7. Run the command: ``createdb `whoami` ``
8. Connect to your postgres with the command: `psql`

## Details
### What is this `ln` command I ran in my Terminal?

_from the `man ln` command_

> The ln utility creates a new directory entry (linked file) which has the same modes as the original file.  It is useful for maintaining multiple copies of a
     file in many places at once without using up storage for the ``copies''; instead, a link ``points'' to the original copy.  There are two types of links; hard
     links and symbolic links.  How a link ``points'' to a file is one of the differences between a hard and symbolic link.

### What is `launchctl`?

_from the `man launchctl` command_

>launchctl interfaces with launchd to manage and inspect daemons, angents and XPC services.
