# powerline-setup
powerline setup on osx


## PATH issue

```
powerline-config shell command
```

use `$HOME` insted of `~` when adding virtulenv to `PATH`

```
export VIRTUAL_ENV="$HOME/.virtualenv"
export PATH="$VIRTUAL_ENV/bin:$PATH"
```

## scripts

```
from powerline.lib.shell import which

print "searching powerline in PATH ..."
which("powerline")
print "DONE"
```

```
#!/bin/bash

clean() {
  rm -rf  ~/.config/powerline
  mkdir -p ~/.config/powerline

}

install_pwl() {
        local VERSION=$1
        : ${VERSION:? powerline git version is required}

        clean
        pip install git+git://github.com/powerline/powerline@${VERSION}
        cp -r ~/.virtualenv/lib/python2.7/site-packages/powerline/config_files/* ~/.config/powerline/
}

main() {
  install_pwl $1
}

[[ "$0" == "$BASH_SOURCE" ]] && main "$@"
```

```
powerline-config tmux setup
```
