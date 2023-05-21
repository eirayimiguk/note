# ghq + peco

key-bind: C-g

## Install

- [golang](https://go.dev/doc/install)
- [ghq](https://github.com/x-motemen/ghq)
    ```bash
    $ go install github.com/x-motemen/ghq@latest
    ```
- [peco](https://github.com/peco/peco)
    ```bash
    $ sudo apt install peco
    ```

## Settings

### ~/.bashrc

```bash
function ghql() {
  local selected_file=$(ghq list --full-path | peco --query "$LBUFFER")
  if [ -n "$selected_file" ]; then
    if [ -t 1 ]; then
      echo ${selected_file}
      cd ${selected_file}
      pwd
    fi
  fi
}

bind -x '"\201": ghql'
bind '"\C-g":"\201\C-m"'
```

