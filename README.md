# Visual Studio Code For PHP Developers

 
<p align="center"><img src="./images/vscode.png" width="400"></p>

###  Shortcuts

    Command Mode = Ctrl + Shift + p 
    Focuses on Explorer = ctrl + 0
    Move Selected Lines = alt + up / down
    Hide tree view = Ctrl + B 

    Explorer  = Ctrl + shift + E
    Version Control (Git)  = Ctrl + shift + v
    Search = Ctrl + shift + f 
    Debugger = ctrl + shift + d
    Extensions  = Ctrl + shift + x

    Key Binding  = Ctrl + K + S 
    Setting = Ctrl + ,  
    Terminal = Ctrl + ~ 
    Go to Line = ctrl + G  | ctrl + p ---> type :
    Split Screen = Ctrl+\   (switch between them ctrl+1 , ctrl+2 , ...)

    Select current line = Ctrl+L
    Select All Occurrences of selected word = crtl + shift + L
    Select Match To Selected Text = Ctrl + d (for next one one again press ctrl + d)
    Multiple Cursor: alt + mouse left

    Next or Previous Method or Tag = ctrl + up arrow key Or down arrow key
    File All References = alt + shift + F12
    Go to Symbol in File = ctrl + shift + O  | | ctrl + p ---> type @
    Go to Symbol in Workspace = Ctrl + T
    Go to Implementation = ctrl + F12
    Peek = shift + F12

    Expand Selection =  Shift+Alt+Left or Shift+Alt+Right
    Code Folding = Ctrl+Shift+[ OR  Ctrl+Shift+]
    Line Height = crtl + ,  ---> search for line Height then -----> set to 40
    Open Markdown preview = Ctrl + Shift + V

    Duplicate Line Up = Ctrl + Alt + Shift + 8
    Duplicate Line Down : Ctrl + Alt + Shift + 2
    Delete Line: Ctrl + Shift + K 

    Code Formatting:
        Ubuntu = Ctrl + Shift + I
        Windows = Shift + Alt + F
        MacOS = Shift + Option + 

    Change Workspace = ctrl + r    

    List of all files open in an editor group: ctrl + tab
    Focus Breadcrumbs =  ctrl + shift + . 
    Bracket matching = Ctrl + Shift + \
    Switch to previous open file = ctrl + p + ctrl + p
    Open Reference = ctrl + shift + mouse left
    Goto Previous Edit point = ctrl + alt + -
    Shrink/expand selection = Shift+Alt+Right or Shift+Alt+LEFT
    Column (box) selection = Place the cursor in one corner and then hold Shift+Alt while dragging to the opposite corner
    Close panel =  ctrl + j


### Gitlens shoirtcut issue

set `gitlens.keymap` to `none`.

    {   "key": "ctrl+shift+g",   "command": "gitlens.views.repositories:explorer.focus" }

    OR

    {   "key": "ctrl+shift+g",   "command": "gitlens.showRepositoriesView" }

### Settings

    - Enable auto save:  ctrl + ,  ---> search for auto save
    - Disable built-in PHP support:

        ` To disable the built-in PHP smart completions in favor of suggestions from an installed
          PHP extension, uncheck PHP > Suggest: Basic, which sets php.suggest.basic to false in your settings.json file. `
    - Open files in new tab = "workbench.editor.enablePreview": false
    - Hidden Menu Bar = ctrl + shift + p  ---> Toggle Menu Bar
    - Remove Visual Studio Code from title bar = goto settings and search for '"window.title": "${activeEditorLong}"' then remove appName.
    - Ctrl + Click goto definition: "editor.gotoLocation.multipleDefinitions": "goto"
    - Search in git ignore files: set `search.useIgnoreFiles` to false

### Font

        "editor.fontFamily": "'Fira Code', 'Droid Sans Mono', 'monospace', monospace, 'Droid Sans Fallback'",
        "editor.fontLigatures": true,

### Debugging

#### Install Xdebug

    sudo apt install php-xdebug

Then run sudo nano /etc/php/7.2/mods-available/xdebug.ini and add the following lines:

    xdebug.remote_enable = 1
    xdebug.remote_autostart = 1
    xdebug.remote_host = x.x.x.x # for docker

#### Xdebug plugin

    felixfbecker.php-debug


![xdebug](./images/xdebug1.gif)
![xdebug](./images/xdebug2.gif)


#### Configure Xdebug to open file links with VS Code

 When you encounter an error, or when you use the Symfony debug toolbar or the profiler, you may want toopen the desired file directly in your IDE with the cursor at the corresponding line.

To be able to do that, you need to add the following line to your /etc/php/7.2/mods-available/xdebug.ini:

    xdebug.file_link_format = vscode://file/%f:%l

    xdebug.file_link_format = 'vscode://file/%f:%l&/path/to/app/in/docker/>/path/to/app/on/host/' # docker version

![xdebug](./images/xdebug3.gif)


### PHP CS Fixer

    composer global require friendsofphp/php-cs-fixer


#### plugin

    junstyle.php-cs-fixer

#### settings

    "[php]": {
        "editor.defaultFormatter": "junstyle.php-cs-fixer",
        "editor.formatOnSave": true
    },

![xdebug](./images/php-cs-fixer.gif)

#### PHP CS Fixer config file

If you want to disable or enable some specific linting rules, you can do it in a .php_cs file at the root folder of your project. If this configuration file is present, VS Code takes it into account and overrides the configuration found in settings.json. You can find more information about the .php_cs file in the GitHub repository. A simple config file to use @PhpCsFixer category and disable some rules could be:


```php 
    <?php

    return PhpCsFixer\Config::create()
        ->setRules([
            '@PhpCsFixer' => true,
            'php_unit_internal_class' => false,
            'php_unit_test_class_requires_covers' => false,
        ])
    ;
```

#### In case of issues with format on save

Depending on your computer's speed, the length of your files and the number of rules you activate, linting a file on save can be slow, causing VS Code to refuse it. To fix this behavior, change the formatOnSaveTimeout in your settings.json:

    "editor.formatOnSaveTimeout": 5000,


### Tips and Tricks

##### Show List of Extentions

    $ code --list-extensions

##### Install Extention 

    $ code --install-extension <ext-name>

##### Install From File

    $ less extentions.txt | xargs -n 1 code --install-extension

### Awesome Plugins 

    adrianwilczynski.alpine-js-intellisense
    ahinkle.laravel-model-snippets
    alefragnani.Bookmarks
    amiralizadeh9480.laravel-extra-intellisense
    atlassian.atlascode
    auchenberg.vscode-browser-preview
    austenc.tailwind-docs
    BernardXiong.env-vscode
    bmewburn.vscode-intelephense-client
    bradlc.vscode-tailwindcss
    calebporzio.better-phpunit
    christian-kohler.path-intellisense
    CoenraadS.disableligatures
    damianbal.vs-phpclassgen
    DiemasMichiels.emulate
    donjayamanne.jquerysnippets
    eamodio.gitlens
    ecmel.vscode-html-css
    EdgardMessias.clipboard-manager
    Equinusocio.vsc-community-material-theme
    Equinusocio.vsc-material-theme
    equinusocio.vsc-material-theme-icons
    ericadamski.carbon-now-sh
    felixfbecker.php-debug
    formulahendry.auto-close-tag
    formulahendry.auto-rename-tag
    formulahendry.code-runner
    freshbitsweb.laravel-traveller
    GitLab.gitlab-workflow
    humao.rest-client
    ikappas.composer
    iocave.monkey-patch
    jakebathman.mysql-syntax
    jasonn-porch.gitlab-mr
    jock.svg
    junstyle.php-cs-fixer
    kisstkondoros.vscode-gutter-preview
    KnisterPeter.vscode-github
    liuji-jim.vue
    mads-hartmann.bash-ide-vscode
    MehediDracula.php-constructor
    MehediDracula.php-namespace-resolver
    MicroProfile-Community.mp-rest-client-generator-vscode-ext
    MicroProfile-Community.mp-starter-vscode-ext
    MicroProfile-Community.vscode-microprofile-pack
    mikestead.dotenv
    mishkinf.goto-next-previous-member
    ms-azuretools.vscode-docker
    msjsdiag.vscode-react-native
    naumovs.color-highlight
    neilbrayfield.php-docblocker
    octref.vetur
    onecentlin.laravel-blade
    onecentlin.laravel5-snippets
    Open-Liberty.liberty-dev-vscode-ext
    phproberto.vscode-php-getters-setters
    PKief.material-icon-theme
    pnp.polacode
    rebornix.ruby
    redhat.java
    redhat.vscode-quarkus
    redhat.vscode-yaml
    royaction.color-manager
    ryannaddy.laravel-artisan
    sandy081.todotasks
    sensourceinc.vscode-sql-beautify
    shakram02.bash-beautify
    sidharthachatterjee.vscode-tailwindcss
    sleistner.vscode-fileutils
    steoates.autoimport
    streetsidesoftware.code-spell-checker
    techer.open-in-browser
    thekalinga.bootstrap4-vscode
    thisotherthing.vscode-todo-list
    tht13.html-preview-vscode
    urbantrout.refactor-css
    vscjava.vscode-java-debug
    vscode-icons-team.vscode-icons
    wingrunr21.vscode-ruby
    ypresto.vscode-intelli-refactor
    Zaczero.bootstrap-v4-snippets



### Keybindings

// Place your key bindings in this file to override the defaults
[
    {
        "key": "ctrl+shift+c",
        "command": "clipboard-manager.editor.pickAndPaste",
        "when": "textInputFocus && !editorReadonly"
    },
    {
        "key": "ctrl+shift+v",
        "command": "-clipboard-manager.editor.pickAndPaste",
        "when": "textInputFocus && !editorReadonly"
    },
    {
        "key": "ctrl+shift+m ctrl+shift+m",
        "command": "markdown.showPreview",
        "when": "editorLangId == 'markdown'"
    },
    {
        "key": "ctrl+shift+v",
        "command": "-markdown.showPreview",
        "when": "editorLangId == 'markdown'"
    },
    {
        "key": "ctrl+shift+v",
        "command": "-workbench.action.terminal.paste",
        "when": "terminalFocus"
    },
    {
        "key": "shift+alt+p",
        "command": "better-phpunit.run"
    },
    {
        "key": "meta+k meta+r",
        "command": "-better-phpunit.run"
    },
    {
        "key": "ctrl+shift+alt+p",
        "command": "better-phpunit.run-previous"
    },
    {
        "key": "meta+k meta+p",
        "command": "-better-phpunit.run-previous"
    },
    {
        "key": "ctrl+e",
        "command": "-workbench.action.quickOpen"
    },
    {
        "key": "ctrl+e",
        "command": "-workbench.action.quickOpenNavigateNextInFilePicker",
        "when": "inFilesPicker && inQuickOpen"
    },
    {
        "key": "ctrl+shift+g shift+b",
        "command": "-gitlens.toggleCodeLens",
        "when": "editorTextFocus && gitlens:canToggleCodeLens && gitlens:enabled && config.gitlens.keymap == 'chorded'"
    },
    {
        "key": "ctrl+shift+g b",
        "command": "-gitlens.toggleFileBlame",
        "when": "editorTextFocus && config.gitlens.keymap == 'chorded' && gitlens:activeFileStatus =~ /blameable/"
    },
    {
        "key": "ctrl+shift+g s",
        "command": "-gitlens.showQuickRepoStatus",
        "when": "gitlens:enabled && config.gitlens.keymap == 'chorded'"
    },
    {
        "key": "ctrl+shift+g h",
        "command": "-gitlens.showQuickFileHistory",
        "when": "gitlens:enabled && config.gitlens.keymap == 'chorded'"
    },
    {
        "key": "ctrl+shift+g .",
        "command": "-gitlens.diffWithNext",
        "when": "editorTextFocus && !isInDiffEditor && config.gitlens.keymap == 'chorded' && gitlens:activeFileStatus =~ /revision/ && gitlens:activeFileStatus =~ /revision/"
    },
    {
        "key": "ctrl+shift+g ,",
        "command": "-gitlens.diffWithPrevious",
        "when": "editorTextFocus && isInDiffLeftEditor && config.gitlens.keymap == 'chorded' && gitlens:activeFileStatus =~ /tracked/"
    },
    {
        "key": "ctrl+shift+g -",
        "command": "-gitlens.showLastQuickPick",
        "when": "gitlens:enabled && config.gitlens.keymap == 'chorded'"
    },
    {
        "key": "ctrl+shift+g shift+h",
        "command": "-gitlens.showQuickRepoHistory",
        "when": "gitlens:enabled && config.gitlens.keymap == 'chorded'"
    },
    {
        "key": "ctrl+shift+g /",
        "command": "-gitlens.showCommitSearch",
        "when": "gitlens:enabled && config.gitlens.keymap == 'chorded'"
    },
    {
        "key": "ctrl+shift+g w",
        "command": "-gitlens.diffLineWithWorking",
        "when": "editorTextFocus && config.gitlens.keymap == 'chorded' && gitlens:activeFileStatus =~ /tracked/"
    },
    {
        "key": "ctrl+shift+g [IntlBackslash]",
        "command": "-gitlens.diffLineWithPrevious",
        "when": "editorTextFocus && config.gitlens.keymap == 'chorded' && gitlens:activeFileStatus =~ /tracked/"
    },
    {
        "key": "ctrl+shift+g shift+,",
        "command": "-gitlens.diffLineWithPrevious",
        "when": "editorTextFocus && config.gitlens.keymap == 'chorded' && gitlens:activeFileStatus =~ /tracked/"
    },
    {
        "key": "ctrl+shift+g c",
        "command": "-gitlens.showQuickCommitFileDetails",
        "when": "editorTextFocus && gitlens:enabled && config.gitlens.keymap == 'chorded'"
    },
    {
        "key": "ctrl+shift+g shift+.",
        "command": "-gitlens.diffWithWorking",
        "when": "editorTextFocus && config.gitlens.keymap == 'chorded' && gitlens:activeFileStatus =~ /revision/"
    },
    {
        "key": "ctrl+shift+g ,",
        "command": "-gitlens.diffWithPreviousInDiffRight",
        "when": "editorTextFocus && isInDiffRightEditor && config.gitlens.keymap == 'chorded' && gitlens:activeFileStatus =~ /tracked/"
    },
    {
        "key": "ctrl+shift+g ,",
        "command": "-gitlens.diffWithPrevious",
        "when": "editorTextFocus && !isInDiffEditor && config.gitlens.keymap == 'chorded' && gitlens:activeFileStatus =~ /tracked/"
    },
    {
        "key": "ctrl+shift+g .",
        "command": "-gitlens.diffWithNextInDiffLeft",
        "when": "editorTextFocus && isInDiffLeftEditor && config.gitlens.keymap == 'chorded' && gitlens:activeFileStatus =~ /revision/ && gitlens:activeFileStatus =~ /revision/"
    },
    {
        "key": "ctrl+shift+g .",
        "command": "-gitlens.diffWithNext",
        "when": "editorTextFocus && isInDiffRightEditor && config.gitlens.keymap == 'chorded' && gitlens:activeFileStatus =~ /revision/ && gitlens:activeFileStatus =~ /revision/"
    },
    {
        "key": "ctrl+shift+g g",
        "command": "-workbench.view.scm",
        "when": "gitlens:enabled && config.gitlens.keymap == 'chorded'"
    },
    {
        "key": "ctrl+shift+g",
        "command": "-workbench.view.scm"
    },
    {
        "key": "ctrl+shift+g",
        "command": "gitlens.views.repositories:explorer.focus"
    }
]