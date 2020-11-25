# Environment Variables

These exist globally on a specific environment or a machine. One generally doesn't want to have too many of them. They can be interpolated into code and other services.


## Variables In Bash

* To declare (generally use uppercase as is convention)
	* No spaces
```sh
VAR_NAME=chicken
```

* To see:
```sh
echo $VAR_NAME

# or just

$VAR_NAME
```

* Can assign commands output to variables:
```sh
VAR_NAME=$(pwd)
```

* **These only stay in this terminal, or as long as this terminal (current) session is open**

## Child Process

When terminal runs another file or bash script, it makes a child process.

## Export

* You can use `export` to make a variable available to child processes
	* Wouldn't show the variable, since it needs to be `export` first, then it will be produced

```sh
echo "Chicken chicken chicken"

echo $VAR_NAME
```

## Check Variables

`printenv`
`env`


## Making Variables Persistent In Your Computer

* Reads from `.bash_profile` and then `.bashrc` in order
	* /etc/ then in users home directory (`~/`)

* This should be in `.profile` by default usually, tells it to check `.bashrc` if available`
```sh
# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi
```

* Make a variable permanent
```sh
export VAR_NAME=something
```

