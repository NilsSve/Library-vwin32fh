# vwin32fh - This library has been forked from the original vwin32fh repository on GitHub.
This is a library that is used by main repositories on the NilsSve site (not libraries)! It is being installed automatically when selecting to clone a regular repository.

From VDF-GUIdance: vWin32fh WINAPI file handling
Uploaded to GitHub to make it easy to add as a submodule

For the latest, always check https://www.vdf-guidance.com/ContribPage.asp?Page=PKGWINAPIVWIN32F&ContribRecId=80

## Dependencies

None. vwin32fh is a leaf - nothing here reaches into another RDC library. It is the bottom of
the dependency graph: RDCToolsLib needs it, and DUF needs it both directly and through
RDCToolsLib. Keep it dependency-free.

Note that `vWin32fh.pkg` is the only entry point you should `Use`. It picks between
`vWin32fhA.pkg` (ANSI) and `vWin32fhW.pkg` (Unicode) with a `#IF (!@ < 200)`; `Use`ing either of
those directly, or both, defeats that and collides.

## Compiling it on its own

`FileHandlingDemo.src` already serves as the canary - it is a real program that exercises the
package, so a plain compile of it verifies the library standalone. No extra smoke test needed
here.

# From original readme.txt:
My apologies for using Visual DataFlex Libraries in a very unconvential way.

For a minimum class library the standard file layout is a bit overkill.
Usually there are no data files, no IdeSrc required, no bitmaps etc.. just a few packages.

By putting the library meta data files in a subfolder and having the packages at the top, the focus stays on the code.

When adding the packages as a library, just select the .sws file version that is for your DataFlex version and it should all work as normal.

You can find the .sws files in the StudioLibrary folder (as is the other meta data stuff)
