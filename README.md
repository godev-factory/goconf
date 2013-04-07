goconf
======
Configuration file parser for the Go Programming Language.
=========================================================
Clone of  https://code.google.com/p/goconf/  Little refactoring , added ``int64`` and ``uint64`` types

Installation
============
You can just link your program to goconf, but it is suggested that you install this library in ```$GOROOT`` with go install.

Go install

Go install will automatically fetch the latest code and it will even update it for you if you tell it to. As soon as the library stabilizes it will only fetch the latest stable release.

go install github.com/postfix/goconf
Then, when you want to use it you just need to ``import "github.com/postfix/goconf"``

Using It
==========
You can use goconf by putting the correct import statement (depending on which of the above methods you used) at the top of the file.

NOTE: All section names and options are case insensitive. All values are case sensitive.

Example 1
=========
Config
```
host = something.com
port = 443
active = true
compression = off
```

```go
c, err := goconf.ReadConfigFile("something.config")
c.GetString("default", "host") // return something.com
c.GetInt("default", "port") // return 443
c.GetBool("default", "active") // return true
c.GetBool("default", "compression") // return false
```

Example 2
=========
Config
```
[default]
host = something.com
port = 443
active = true
compression = off

[service-1]
compression = on

[service-2]
port = 444
```
Code
====

```go
c, err := goconf.ReadConfigFile("something.config")
c.GetBool("default", "compression") // returns false
c.GetBool("service-1", "compression") // returns true
c.GetBool("service-2", "compression") // returns GetError
```


Types
======
```go
c.GetString // retrun string 
c.GetBool   // return false or true
c.GetInt    // return Int
c.GetFloat64  // return Float64
c.GetInt64   // return Int64
c.GetUint64  // return Uint64 
```
Comment prefixes ```  # or ;```

More Documentation
==================
You can get more documentation by using godoc. Just run ```godoc -http=:6060```
