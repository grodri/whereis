# whereis

The `whereis` Stata command is used to keep track of external programs as well as ancillary files and folders. 

## Syntax

The syntax of the command is

```
whereis [name [location]]
```

The `name` argument specifies the name of the resource. It must be a single word conforming to Stata conventions for variable names, with no spaces.

The `location` argument is used when registering a resource and should be a full path specifying the location of the file or folder. This must conform to Stata conventions for file names. In particular, it should be enclosed in quotes if it includes spaces.

When the command is called with a `name` and `location` it checks that the location corresponds to an existing file or folder, and updates or creates an entry in its own directory.

If only a `name`' is specified, the command retrieves the `location`and checks that the file or folder exists. In both cases the location is stored in a local macro `r(name)` using the name of the resource.

If the command is called with no arguments it lists all registered resources.

The resources are stored in a text file called `whereis.dir`, created in the same location as `whereis` itself. This is typically the PLUS folder and you need to have write access to it.

## Applications

The original motivation for the command was to store the location of external programs without cluttering the path. Suppose for example you need to run Pandoc from Stata. After installing Pandoc, you register its location with `whereis`.  For example on a Mac you may issue the command 

```
whereis pandoc /usr/local/bin/pandoc
```

To run Pandoc from Stata you can call `whereis pandoc` and retrieve the location from the macro `r(pandoc)`.  When you shell out, make sure you enclose the location in quotes just in case it includes spaces. This is the mechanism used by `markstat` to run Pandoc.

The command may also be used to store folders, a suggestion due to Diana Goldemberg, who also indicated how to modify the code to enable this extension. Her team uses Dropbox and Github a common directory structure for each project, but each member has a different local root. Storing the root Dropbox or Github folder with `whereis` allows all team members to use the same code to access the files.

## Installation

The `whereis` command is available from the Statistical Software Components (SSC) archive, and can be installed by typing in Stata

```
ssc install whereis
```

The current version is 1.4 and was made available through SSC on 28 Feb 2020.

