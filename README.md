<!--

    Copyright (c) 2008-present Sonatype, Inc.

    All rights reserved. Includes the third-party code listed at http://links.sonatype.com/products/nexus/pro/attributions
    Sonatype and Sonatype Nexus are trademarks of Sonatype, Inc. Apache Maven is a trademark of the Apache Foundation.
    M2Eclipse is a trademark of the Eclipse Foundation. All other trademarks are the property of their respective owners.

-->

# bower-nexus3-resolver

An NPM package for integrating the Nexus 3 Repository Manager with Bower (<https://bower.herokuapp.com>). 

## Building the package from source

Run the `npm install` command to pull down any necessary dependencies.

Run the associated Mocha tests by invoking `npm test`. The output is displayed to the console, and the command will
return a nonzero result code in the event of test failure.

Run the `npm pack` command to produce a .tgz containing the package contents.

You also have the option of using Maven to generate the .tgz package and test reports by performing a Maven build
of the module. The outputs will be placed in the `target` subdirectory similar to standard Maven builds. 

You can also build as part of a build of the entire project by specifying the `-Pinclude-bower-resolver` option.

## Installation

You will likely want to install the resolver globally. To install from the provided .tgz, use:

    npm install -g bower-nexus3-resolver-version.tgz

Once published to npm, you should be able to install the published version by using:

    npm install -g bower-nexus3-resolver

You may also install the resolver on a per-project basis instead by adding it as a devDependency in your `package.json`:

    "devDependencies" : {
      "bower-nexus3-resolver" : "*"
    }

## Setup

Use the resolver by configuring your `.bowerrc` file with the URL for the Bower registry in Nexus:

    {
      "registry" : "http://host:port/repository/your-bower-repo",
      "resolvers" : [
        "bower-nexus3-resolver"
      ]
    }

At that point, you should be ready to install Bower packages via Nexus. 

If you are including the resolver on a per-project basis, remember to run `npm install` on your project after updating 
the dependencies to ensure the resolver has been installed locally.

## Authentication

Authentication for the registry itself can be performed by specifying the username and password in the URL:

    {
      "registry" : "http://username:password@host:port/repository/your-bower-repo"
    }

If you are concerned about authentication, you will also want to specify a Nexus username and password for `nexus` URLS:

    {
       "nexus" : {
          "username" : "myusername"
          "password" : "mypassword"
       }
    }

## HTTPS support

The resolver supports the `strict-ssl` flag in the `.bowerrc` configuration. To disable strict SSL (such as for working
with self-signed certificates), you may set this option to `false`:

    {
       "strict-ssl" : false
    }

## Working on the resolver

If you're working on the resolver itself, rather than using it in a project's build, you'll want to run `npm link` for 
the resolver and `npm link bower-nexus3-resolver` in the project under test.

## License

```
Copyright (c) 2008-present Sonatype, Inc.

All rights reserved. Includes the third-party code listed at http://links.sonatype.com/products/nexus/pro/attributions
Sonatype and Sonatype Nexus are trademarks of Sonatype, Inc. Apache Maven is a trademark of the Apache Foundation.
M2Eclipse is a trademark of the Eclipse Foundation. All other trademarks are the property of their respective owners.
```
