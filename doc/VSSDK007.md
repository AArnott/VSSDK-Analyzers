# VSSDK007 Avoid using SxS assemblies for exchange types

The Managed Package Framework (MPF) is defined in the Microsoft.VisualStudio.Shell.15.0.dll assembly
(or equivalent in earlier versions). Each major release of Visual Studio ships a *new* version
of this assembly, in addition to all the versions from past major releases.
No binding redirects consolidate the types from the old versions to the newest version.

As a result, any use of these side-by-side assemblies should be kept as an
implementation detail of your VS extension. Exposing a type from an MPF assembly
in your public API, or casting an object obtained from another assembly to an MPF type,
can lead to a runtime failure when the other assembly compiled against a different
major version of MPF.

## Examples of patterns that are flagged by this analyzer



## Solution


