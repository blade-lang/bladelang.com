# Publishing packages

Nyssa packages are simply nyssa projects published on a Nyssa repository. This document highlights the steps and guides to publishing a package to a repository.

## Package name guidelines

Before publishing a package, there are a few things you should consider when choosing a package name.

1. It must be unique. Package names are unique throughout a repository irrespective of who publishes them. 
  
  It is advisable to first search the repository you want to publish to (such as [nyssa.bladelang.org](nyssa.bladelang.org)) for any package already using the name you want to choose. 
  
  > It is also highly possible but not conventional to have the same package published under different names in different repositories.
2. It should be descriptive.
3. It should not infringe on a someone else's trademarks nor be misleading.

Also, a good package names should be useable as a good variable names.

## The README.md file

One of the files generated by nyssa during `nyssa init` is the `README.md` file. Before publishing a package, do your best to communicate as much information and/or documentation as you can in this file because this is the file that will be shown to people who come to browse your package on repositories.

> The file is a Markdown file and should be treated as such. You can check Github's guide on [Markdown](https://guides.github.com/features/mastering-markdown/#what) to help you write more appealing READMEs.

## Semantic versioning

Everytime you publish a new package or an update to an existing package, nyssa _requires_ that the package version changes as well. Following the semantic versioning when changing/updating this version helps keep the ecosystem clean and predictable as well as easy to navigate for other developers.

When introducing a breaking change to a package, it's recommended that you increment the major version of the package.

## Publishing to a repository

Before you can publish an application, you must have created and be logged in to a publisher account. See [this guide](/nyssa/publishers-account) on how to do that.

Once you are logged in to your publisher account, simply run the command `nyssa publish` from the root of your package and nyssa will take care of the rest.

## Testing your package

One very important first things to do after publishing a package is testing that the package actually works and is importable in other applications without causing a crash or undesired side-effects.

To test your application after publising to a repository,

- Create a new directory outside of your project (e.g. `sample`) and open a new terminal session in the directory. This can be done on Unix devices like this:

```
mkdir sample
cd sample
```

- Create a new nyssa application in the directory by running `nyssa init`.
- Run the command `nyssa install <package_name>`.
- Open the file at `app/index.b` and insert code to import your package before every code in the file. E.g.

```blade
import <package_name>
echo 'Welcome to Nyssa. Magic begins here!'
```

- Run the application (`blade .`)

If all goes well without crashing, then your package can be imported without crashing the user's application. From here on, you can write more tests.

> In this example, the package_name was `my_package`.
