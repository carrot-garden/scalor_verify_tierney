# tierney

[![Build Status](https://travis-ci.org/m50d/tierney.svg?branch=master)](https://travis-ci.org/m50d/tierney)

Generic structured commands with explicit parallelism
 
## How to use

### Add the dependency

    <dependency>
		<groupId>com.github.m50d</groupId>
		<artifactId>tierney-core</artifactId>
		<version>0.3</version>
	</dependency>

### Direct use with `Future` or `Task`

TODO

### Use with custom command type and interpreter

TODO

## Information for developers

### Features required for 1.0

 * Add rationale to this document, including comparison to the talk about this kind of thing if I can find it
 * Write tests for interleaved serial/parallel flows
 * Write examples in the this document
 
### Other planned features

 * Add `tut-maven-plugin` (once implemented) to enforce that code examples in this document are correct

### Current project layout

 * Higher-kinded variants of some general constructs as necessary to support the rest of the project
   (`core`, potentially to be replaced with use of polykinds from Typelevel Scala)
 * Recursion-schemes style `Fix`/`FixK`/... constructs and traversal implementations
   (currently also `core`, potentially to be spun out into a separate module if the above remains necessary)
 * `ParallelApplicative` type to express explicit, intentional parallelism
   (`free`, potentially to be spun out into a separate module)
   * Implementations for common cases (stdlib `Future`, monix `Task`, fs2 `Task`),
     potentially to be spun out into their own modules to minimize dependencies
 * Implementation of a free hybrid monad-applicative structure, making use of all the above (`free`)
 
### How to develop in Eclipse

 1. Usual Eclipse Scala development setup:
  1. Unzip Eclipse
  1. Install scala-ide plugin
  1. Install m2eclipse-scala plugin
  1. Install maven scm connector for git (possibly bundled in recent versions of eclipse)
 1. File > Import ... , Maven > Check Out Maven Projects from SCM
 1. Enter the clone URL from GitHub
 1. Click Next, then Finish immediately i.e. skip as much of the wizard as possible
 1. For each project:
  1. Right click > Properties, Scala Compiler
   1. Advanced tab, XPlugin box: fill in the full path to `kind-projector[...].jar`
   1. Build manager tab, untick "withVersionClasspathValidator" as it is overly sensitive to patch versions for compiler plugins