# Sublime Text Setup

These are the steps needed to set up [Sublime Text](http://www.sublimetext.com/). Instructions are for Linux; OS X and Windows users should make substitutions as necessary. (This may require web searches. Please let me know if you find something that you think should be included here.)

## Command-line Command

### Linux

On Linux (especially Ubuntu), you may have Sublime Text on your repos; if not you can set up `subl` as a command-line command like this:

    $ sudo ln -s ~/Applications/Sublime\ Text\ 3/sublime_text /usr/bin/subl

Check that you must use `sudo`, it is required because ordinary users don't have permission to write to `/usr/bin`. Alternatively, add an alias to `sumblime_text` in your `~/.bashrc` file.  This method doesn't require `sudo`. But it assumes you are using `bash`. There are similar methods available for other shells. Google is your friend.

Use any editor like vim or gedit to open `~/.bashrc`.
    
    $ vim ~/.bashrc
    
Add `alias subl='~/Applications/Sublime\ Text\ 3/sublime_text'` at the end of the file. Save and exit.

(You may have to replace the path to `sublime_text` with the correct one for your system.)

On Linux Mint, take a look at [Install Sublime Text in Linux Mint](http://blog.hugeaim.com/2012/03/13/install-sublime-text-2-in-linux-mint/).

### OS X

On OS X, you can set up `subl` as a command-line command like this:

    $ ln -s "/Applications/Sublime Text 3.app/Contents/SharedSupport/bin/subl" ~/bin/subl

This assumes that there is a `~/bin` directory on your executable path.

### Windows

On Windows, you can simply double-click the application icon. The setup at the command line depends on which shell you use; see if one of the techinques at the [Stack Overflow discussion on Sublime Text from Command Line (Win7)](http://stackoverflow.com/questions/9440639/sublime-text-from-command-line-win7) works for you. You might also want to check out the video [Easily Open Files from Windows Command Prompt with Sublime Text 2](http://youtu.be/zcUpdw5_uSY) (I suggest changing `st2` to `subl` to be consistent with the instructions for the other platforms).

## Basic configuration

Open up Sublime Text and use the `View` menu to modify the following settings:

`View > Hide Minimap`

`View > Side Bar > Hide Side Bar`

`View > Layout > Columns: 2`

## Copy auxiliary files

    $ cd /tmp
    $ git clone https://github.com/agpelliza/sublime_text_setup.git

Setup on Linux:

    $ cp -r sublime_text_setup/* \
            ~/.config/sublime-text-3/Packages/

On OS X is similar, but with a different target directory for `cp`:

    $ cp -r sublime_text_setup/* \
            ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/

On Windows, the target directory is as follows:

    $ cp -r .\sublime_text_setup\* \
            '~\AppData\Roaming\Sublime Text 3\Packages\'

Note: If using Windows Vista, 7, or 8, you should first copy all the folders and files from the remote repo into your local temporary folder located at `C:\Users\User\AppData\Local\Temp`. Then proceed to move these same files to `C:\Users\User\AppData\Roaming\Sublime Text 3\Packages\User`.

Finally, restart Sublime Text.

## Set up the theme

Select `Preferences > Color Scheme > User > Railscasts`

## Keyboard mappings

The default keyboard settings use the **Escape** key for autocompletion. To use the **tab** key instead you will need to add some complex custom keyboard mappings:

Select `Preferences > "Key Bindings - User"` and copy the bindings found in `Autocompletion/Tabs.sublime-keymap`.

Also, to anable the ERB toggle command in all file add the following keybinding:

```json
  [
    { "keys": ["ctrl+shift+."], "command": "erb" }
  ]
```

...or if you only want the most common ERB contexts:

```json
  [
    { "keys": ["ctrl+shift+."], "command": "erb", "context":
      [
        { "key": "selector", "operator": "equal", "operand": "text.html.ruby, text.haml, source.yaml, source.css, source.scss, source.js, source.coffee" }
      ]
    }
  ]
```

Now you can use `ctrl+shift+.` to create and toggle between ERB tags.
NOTE: On a Mac use the command key for the ctrl key.