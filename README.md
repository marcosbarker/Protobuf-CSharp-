# Protobuf-CSharp
Protobuf em C# - Implementação do exemplo base da documentação Developers Google

This directory contains the C# Protocol Buffers runtime library.

Usage
=====

The easiest way how to use C# protobufs is via the `Google.Protobuf`
NuGet package. Just add the NuGet package to your VS project.

You will also want to install the `Google.Protobuf.Tools` NuGet package, which
contains precompiled version of `protoc.exe` and a copy of well known `.proto`
files under the package's `tools` directory.

To generate C# files from your `.proto` files, invoke `protoc` with the
`--csharp_out` option.

Supported platforms
===================

The runtime library is built as a portable class library, supporting:

- .NET 4.5
- Windows 8
- Windows Phone Silverlight 8
- Windows Phone 8.1
- .NET Core

You should be able to use Protocol Buffers in Visual Studio 2012 and
all later versions. This includes all code generated by `protoc`,
which only uses features from C# 3 and earlier.

Building
========

Open the `src/Google.Protobuf.sln` solution in Visual Studio 2017 or
later.

Although *users* of this project are only expected to have Visual
Studio 2012 or later, *developers* of the library are required to
have Visual Studio 2017 or later, as the library uses C# 6 features
in its implementation, as well as the new Visual Studio 2017 csproj
format. These features have no impact when using the compiled code -
they're only relevant when building the `Google.Protobuf` assembly.

In order to run and debug the AddressBook example in the IDE, you must
install the optional component, ".Net Core 1.0 - 1.1 development tools
for Web" (as it's labelled in current versions of the VS2017
installer), above and beyond the main .NET Core cross-platform
development feature.

Testing
=======

The unit tests use [NUnit 3](https://github.com/nunit/nunit). Tests can be
run using the Visual Studio Test Explorer or `dotnet test`.

.NET 3.5
========

We don't officially support .NET 3.5. However, there has been some effort
to make enabling .NET 3.5 support relatively painless in case you require it.
There's no guarantee that this will continue in the future, so rely on .NET
3.5 support at your peril.

To enable .NET 3.5 support, you must edit the `TargetFrameworks` elements of
[src/Google.Protobuf/Google.Protobuf.csproj](src/Google.Protobuf/Google.Protobuf.csproj)
(and [src/Google.Protobuf.Test/Google.Protobuf.Test.csproj](src/Google.Protobuf.Test/Google.Protobuf.Test.csproj)
if you want to run the unit tests):

Open the .csproj file in a text editor and simply add `net35` to the list of
target frameworks, noting that the `TargetFrameworks` element appears twice in
the file (once in the first `PropertyGroup` element, and again in the second
`PropertyGroup` element, i.e., the one with the conditional).

History of C# protobufs
=======================

This subtree was originally imported from https://github.com/jskeet/protobuf-csharp-port
and represents the latest development version of C# protobufs, that will now be developed
and maintained by Google. All the development will be done in open, under this repository
(https://github.com/protocolbuffers/protobuf).

The previous project differs from this project in a number of ways:

- The old code only supported proto2; the new code only supports
proto3 (so no unknown fields, no required/optional distinction, no
extensions)
- The old code was based on immutable message types and builders for
them
- The old code did not support maps or `oneof`
- The old code had its own JSON representation, whereas the new code
uses the standard protobuf JSON representation
- The old code had no notion of the "well-known types" which have
special support in the new code
- The old project supported some older platforms (such as older
versions of Silverlight) which are not currently supported in the
new project
