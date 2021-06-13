Go Cheat Sheet
==============

Install Go on Mac
-----------------

> Following the instructions from https://golang.org/doc/install

1. Download https://golang.org/doc/install?download=go1.13.3.darwin-amd64.pkg
1. Run installer

> if you don't set a `$GOPATH`, the default path is `~/go`


Go Modules
----------

### Basic Commands

> Remember to work outside of your `$GOPATH`!

* initialize a new module

    ```bash
    export GO111MODULE=on
    go mod init
    ```

  * this will create a `go.mod` file in your current directory.

* add a new dependency

  * in your `.go` file

     ```go
     import rsc.io/quote
     ```

  * build your code

     ```bash
     go build
     ```

  * check your `go.mod` file, it will only show the `rsc.io/quote` module
  * check transitive dependencies with

     ```bash
     go list -m all
     ```

* list versions

   ```bash
   go list -m -versions rsc.io/sampler
   ```

* upgrade modules

  * check available update for all modules via

     ```bash
     go list -m -u all
     ```

  * update one specific package via (will update your dependency in `go.mod`)

     ```bash
     go get -u golang.org/x/text v0.3.0
     ```

  * upgrade all modules

     > might not be a good idea though!

     ```bash
     go get -u
     ```

* downgrading

  *

* use local changes

   ```bash
   # assume the local copy of your module is in ../quote
   go mod edit -replace 'rsc.io/quote=../quote'
   ```

* use remote fork / specific tag

   ```bash
   go mod edit -replace 'rsc.io/quote=github.com/myitcv/london-gophers-quote-fork@0.0.0-myfork'
   ```

* testing

   * all modules involved in your release (test all modules plus transitive dependencies)

      ```bash
      go test -short all
      ```

   * test a single module package

      ```bash
      go test rsc.io/quote/...
      ```

### Convert an existing Project

> Working outside of the `$GOPATH`

* Initialize Go modules inside the project directory

   ```bash
   go mod init
   go mod tidy
   ```

### References for Go mdules

* [Go Modules Documentation on GitHub](https://github.com/golang/go/wiki/Modules#gomod)
* https://www.youtube.com/watch?v=6MbIzJmLz6Q


Language Details
----------------

* [Missing Generics in Go](https://appliedgo.net/generics/)


Go Dependency Management
------------------------

* [Fetching Private Dependencies with Go Modules](https://medium.com/@tim_raymond/fetching-private-dependencies-with-go-modules-1d65afe47c62)


Testing with Go
---------------

* [Tests for Go CLI Applications](http://lucapette.me/writing-integration-tests-for-a-go-cli-application)
* [Ginkgo](https://onsi.github.io/ginkgo/)
* [GoMock](https://github.com/golang/mock)


Learning Go
-----------

* [Pacman with Go](https://github.com/danicat/pacgo)