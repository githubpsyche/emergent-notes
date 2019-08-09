The original emergent installation guide can be a bit hard to parse, and in some ways is distributed across many web pages. I try to produce a more concise guide here. As such, though, it does exclude some details. You can find those at the original guide: https://github.com/emer/emergent/wiki/Install

## Potential Prerequisites
Depending on your OS, you may need some unique prerequisites before you can install emergent. I include notes for the Windows and Mac operating systems.

### Some Windows-specific prerequisites
- Git. To install packages with `go get`, you might need Git; this comes with other considered OSes, but not Windows' command prompt. I got mine at https://git-scm.com/downloads
- A mingw compatible `gcc`. The full installation guide recommends the one here: http://tdm-gcc.tdragon.net/download

### Some Mac-specific prerequisites
- Xcode and relevant header files. You can grab these with two commands:
```
> xcode-select --install
> open /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg
```

## Install Go
Go is the programming language that emergent is written in. The installer can be found at https://golang.org/dl/.

## Install GoGi
GoGi is a 2D and 3D graphical user interface used by emergent. In your terminal, just execute the command `go get github.com/goki/gi` to install the package to your system.

## Install Leabra
The leabra ra25 example code is intended to work as a reasonable starting point for creating one's own simulations.

* First grab the specific package containing our target executable.
```
> go get github.com/emer/leabra
```

* Next execute **within the examples/ra25 directory you've generated** another `go get` command to grab all its dependencies. Your relevant `go` folder where packages are installed is usually located in your home directory by default, or at $GOPATH. Within your `go` folder, the path to your ra25 directory should be at `go/src/github.com/emer/leabra/examples/ra25`.
```
> go get -u ./...
```

## Check if your installation worked
Within the same `go/src/github.com/emer/leabra/examples/ra25` path, execute the command `go run ra25.go`. This should initialize emergent with an interface like the one pictured above. 

That's it! To make your own simulations, copy the ra25.go code to your own repository and modify accordingly. To generate an executable file that can be run directly, instead of calling `go run ra25.go`, use `go build` instead. This should generate an `ra25` executable that you can run with `./ra25`. 
