
# 実行

```bash
chmod 755 ./setting.sh
sh ./setting.sh
```

# 構成

```bash
.
├── README.md
├── ansible.cfg
├── group_vars
│   └── localhost.yml #メンテナンス対象
├── inventory
│   └── localhost
├── localhost.yml #playbook
├── roles
│   ├── dotfiles
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── templates
│   │       ├── template.bash_profile #必要であれば編集
│   │       └── template.bashrc #必要であれば編集
│   ├── homebrew
│   │   └── tasks
│   │       └── main.yml
│   ├── homebrew_cask
│   │   └── tasks
│   │       └── main.yml
│   └── vscode
│       ├── tasks
│       │   └── main.yml
│       └── templates
│           ├── keybindings.json #必要であれば編集
│           └── settings.json #**必要であれば編集**
└── setting.sh
```

# localhost.yml
```bash
echo "code_extensions:" && code --list-extensions | awk '{print "  - "$1}'
echo "homebrew_taps:" && brew tap | awk '{print "  - "$1}'
echo "homebrew_packages:" &&  brew list | awk '{print "  - name: "$1}'
echo "homebrew_cask_packages:" && brew list --cask | awk '{print "  - name: "$1}'
```