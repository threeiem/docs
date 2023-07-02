# Overview

The purpose of this document is to have a place to keep information about packages in Arch Linux.

# Installing Packages

This needs to be here because it is the initial function of every package.

```
sudo pacman -S certbot
```

# Remove Packages

Need to delete a package? Yes.

```
sudo pacman -R js78
```

# Package Dependencies

It can be important to know what dependencies there are with packages. Especially if things are moving around.

## View Package Dependencies - `pactree`

View a package's dependencies.

```
pactree js78
```
This gives a tree of all the dependencies that requested package has (ex. js78):

```
js78
├─gcc-libs
│ └─glibc>=2.27
│   ├─linux-api-headers>=4.10
│   ├─tzdata
│   └─filesystem
│     └─iana-etc
├─readline
│ ├─glibc
│ ├─ncurses
│ │ ├─glibc
│ │ └─gcc-libs
│ └─ncurses provides libncursesw.so=6-64
├─zlib
│ └─glibc
└─bash provides sh
  ├─readline
  ├─readline provides libreadline.so=8-64
  ├─glibc
  └─ncurses

```

## View Dependence on a Package

Most of the time you want to know **what depends on this package**. 
To see this get the dependencies in reverse.
This can tell you if a package is safe to remove.

```
pactree -r js78
```

This will print a tree of packages that depend on the requested package. If there are no dependencies on the `pactree` will just print the name of the package (ex. js78):

```
js78
```
