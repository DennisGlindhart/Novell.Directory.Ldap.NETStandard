# LDAP client library for .NET Standard 2.0

Supported on the .NET Standard 2.0 (https://docs.microsoft.com/en-us/dotnet/articles/standard/library) compatible .NET runtimes: .NET Core, .NET Framework 4.6, Universal Windows Platform, Xamarin.

This fork was made to enable development on Visual Studio 2017 with .NET Standard 2.0 because these are breaking changes to the solution structure of the origianl project. There are no other additions or changes to core functionality other than the fact that you can build it oit in 2017 against .NET Standard 2.0.

It works with any LDAP protocol compatible directory server (including Microsoft Active Directory).

[![Build status](https://ci.appveyor.com/api/projects/status/nabbc061vlumiivs/branch/master?svg=true)](https://ci.appveyor.com/project/dsbenghe/novell-directory-ldap-netstandard/branch/master) - Windows Build<br />
[![Build Status](https://travis-ci.org/dsbenghe/Novell.Directory.Ldap.NETStandard.svg?branch=master)](https://travis-ci.org/dsbenghe/Novell.Directory.Ldap.NETStandard) - Linux Build (includes functional tests & stress tests running against OpenLDAP) <br />
[![NuGet](https://img.shields.io/nuget/v/Novell.Directory.Ldap.NETStandard.svg)](https://www.nuget.org/packages/Novell.Directory.Ldap.NETStandard/)

The library is originaly coming from Novell (https://www.novell.com/developer/ndk/ldap_libraries_for_c_sharp.html) - really old code base - looks like a tool-based conversion from Java - this is the original java code repo http://www.openldap.org/devel/gitweb.cgi?p=openldap-jldap.git;a=summary (first commit in that repo is from 2000 :)) - which explains some of the weirdness of the code base.

The Novell documentation for the original library:
* html: https://www.novell.com/documentation/developer/ldapcsharp/?page=/documentation/developer/ldapcsharp/cnet/data/front.html
* pdf: https://www.novell.com/documentation/developer/ldapcsharp/pdfdoc/cnet/cnet.pdf

First commit in this repo is the original C# source code from Novell. Next around 20 commits are my changes in order to port the code base to run on .NET Standard.

See ChangeLog for summary of changes.

There are a number of basic functional tests which are also run as stress tests (e.g. the functional tests running on multiple threads) running against OpenLDAP on Ubuntu Trusty.

Sample usage

```cs
using (var cn = new LdapConnection())
{
	// connect
	cn.Connect("<<hostname>>", 389);
	// bind with an username and password
	// this how you can verify the password of an user
	cn.Bind("<<userdn>>", "<<userpassword>>");
	// call ldap op
	// cn.Delete("<<userdn>>")
	// cn.Add(<<ldapEntryInstance>>)
}

```

Contributions and bugs reports are welcome.

The library has some samples which are not included in the solution and are in the original state (see original_samples folder) - they may or may not compile on .NET Standard - but they should be compilable on .NET Standard with minimal work.
