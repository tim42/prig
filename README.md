# PRIG

**warning:**: prig is in an early stage of development. while it can be used to generate projects, it is absolutely not mature at all. Currently, only the generation work correctly, but the update, check, repair, ... should not be relied upon. At all.

**warning:**: prig is a shell script. Generators are _not_ part of prig and despite them being run in restricted mode some flaws may still exists. The first goal of prig being **not** the security, please use with caution and always check what you are trying to execute. (this includes configuration files that have bootstrap code and prig itself). Configuration files and prig bootstrap code _does_ perform execution in a **non**-restricted shell code that comes directly from network. If this is not acceptable, you can still use a fully local installation of prig, but this will need some configuration on your part. If this is still not acceptable, prig is definitively not the project you are looking for.

## prig in bullet points

Those disclaimers being done, here what prig is about:
 - remove the cumbersome boilerplate of starting a new project
 - ease the pain of upgrading the build-system / submodules / some other automatable-update-things
 - being optional. prig is just a helper. If removed, the project will still function as before
 - huge capability of configuration. everything is an options. everything can be in the conf.
 - huge modularity: generators perform the work. prig run and update them.
 - helper to generate file from a "template language"
 - portable: bash, git and some other coreutils commands.

## demo

My personal configuration file can be found here: https://gist.github.com/tim42/810b1ed33fe57e1916d587ce9df7e9c8
You can download it and execute it. (and if you haven't already read it, please read and understand the second warning).

It can be executed with the following arguments in order to generate a _test_ project in a _test_ directory:

```
./neam-prig init test test/
```

And if you want to add some submodules from github:

```
./neam-prig --add-dep=tim42/tools --add-dep=CruizeMissile/cml init test test/
```

## help

`prig --help` will print the global options, their current values (if values) and a brief help text

`prig help` will print available command verbs, their usage and options and a brief description

`prig help [cmd]` will print the help message for command `cmd`, its usage and options

a `VERBOSE` environment variable can also be set to `1` (prig print what commands it executes) and `2` (generators also print what commands are executed). Every command's output and return code is also logged in a log file (by default `./prig.log`). When doing a `prig init name directory`, there are two invocation of prig, one in the current directory, one in the sub-directory. Two log files will then be generated.
