# EscherLua - May 24, 2015

Escher (http://escherauth.io) is an authentication protocol, and it's about HTTP request signing. I'm one of the guys
behind this project. Lua (http://www.lua.org/) is a very powerful scripting language from 1993. It is embeddable,
available on very different platforms, and quite fast.

I've already have months of experiences about Escher, worked on the PHP, Ruby, JavaScript, and Python implementations,
helped the Java implementation to born, and created the documentation site.

I have not so much experience about Lua. We have created a smart proxy server with OpenResty (nginx) and Redis, but
it is just some hundred lines of code, nothing difficult. I don't know a lot about a language.

## The goal

The goal of the project is implementing the Lua version of the Escher library. It should be well tested and ready
to use in a project. Having only the request signature and validation is a must have, but it would be great to
support presigned URLs as well.

## The challenges

- It is "proven" that it's not possible to deliver an implementation in 14 hours. We have worked a lot on different
  implementations and it was at least a week of work to have something that is not ready but usable. Seems to be fun
  to try doing it in this short time.
- I don't know Lua enough. I have not yet implemented tests in Lua before, I don't know how creating a Lua library
  should happen. I don't know the differences between standalone Lua and nginx embedded Lua. There are a lot to
  learn here.
- This is my first "formal" personal Hackathon.

## Tasks

- Figure out how writing tests in Lua works. Set up a working TDD environment.
- Use EscherJS's JSON based tests to test this implementation.
- Figure out how a library should be created in Lua, what LuaRocks exactly is.
- Implement a very basic Escher signing scenario (Escher documentation contains a lot of tips).
- Implement a very basic Escher validation scenario.
- Improve, fix the bugs, cover all the test cases, create some example code.
- Use the project with nginx.
- Implement presigned URL creation and validation.

## Progress log

### Hour #1

Good progress so far:

- green tests in Travis
- able to load the JSON testsuite files
- a basic project file structure is ready

Expectation for the next hour:

- header canonicalization, checksum calculation should work for the Vanilla GET test

### Hour #2

Too much time spent on finding library with SHA256 and SHA512 support. These libraries are underdocumented, just calling
the library function intuitively helped.

- a very basic canonicalization is ready
- a "working" library for the Vanilla GET test (only the HMAC algorithm's name is a constant, everything else is calculated)

Expectation for the next hour:

- go with configuration handling
- implement a working stringToSign method

### Hour #3

I forgot that getStringToSign needs date handling, and discovering date handling and a findig a proper library is not a quick
task. It's already 11:18, but it's working.

- selected a good looking date library
- a working stringToSign method is ready, no constants

Expectation for the next hour:

- implement a working generateHeader

### Hour #4

Stucked at calculating the proper hash for the signature. The digesting algorithm is different for this case, and have to
figure out how the library should be used. "It almost works.".

- added the generateHeader method
- don't know yet how close I am to finishing the basic version, if everything goes well it's about figuring out how I have to call the crypto lib

Expectation for the next hour:

- have lunch, get some rest
- figure out how to call the crypto library


