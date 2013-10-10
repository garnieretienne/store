Store
=====

Simple key/value store with namespace in bash.
It store its data using the file system. 
Namespaces are folder, keys are files and value are the content of the file.
The default store folder is `~/store` but can be changed using the env var `STORE_DIR`.

Usage
-----

```
Simple key/value store with namespace in bash.
The default store folder is `~/store` but can be changed using the env var `STORE_DIR`.

Usage: 
  get NAMESPACE|KEY             # Get the value for an individual key or a complete namespace
  set [NAMESPACE/]KEY value     # Set the value for a key
  delete NAMESPACE|KEY          # Delete a key or a complete namespace
```

Example
-------

### Store a value in a key

```bash
$ ./store set foo bar
bar
$ ./store get foo
bar
```

### Store a list of env variables in a namespace

```bash
$ ./store set settings/DATABASE_URL psql://user:name@hostname.domain.tld:123456
psql://user:name@hostname.domain.tld:123456
$ ./store set settings/AWS_ACCESS_KEY_ID XXXXXXXXXXX
XXXXXXXXXXX
$ ./store set settings/AWS_SECRET_ACCESS_KEY XXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXX
$ ./store get settings
AWS_ACCESS_KEY_ID=XXXXXXXXXXX
AWS_SECRET_ACCESS_KEY=XXXXXXXXXXXXXXXXXXXXXXXXXXXX
DATABASE_URL=psql://user:name@hostname.domain.tld:123456
```

### Store a list of domain names in a namespace

```bash
$ ./store set domains/comit.srv2.yuweb.fr
comit.srv2.yuweb.fr
$ ./store set domains/comit.io
comit.io
$ ./store set domains/www.comit.io
www.comit.io
$ ./store get domains
comit.io
comit.srv2.yuweb.fr
www.comit.io
```

### Delete a key

```bash
$ ./store set foo bar
bar
$ ./store delete foo
$ ./store get foo
not found
```

### Delete a namespace

```bash
$ ./store set group/foo bar
bar
$ ./store set group/foo hello
hello
$ ./store delete group
$ ./store get group
not found
```



