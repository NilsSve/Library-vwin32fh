# vwin32fh — Win32 file handling for DataFlex

Windows API file and folder operations as DataFlex global functions: copy, move, rename and delete
files, create and remove directories, test what exists, work with temporary files, and open the
standard Windows folder-browsing dialogs.

This is a fork of the vwin32fh package from
[VDF-GUIdance](https://www.vdf-guidance.com/ContribPage.asp?Page=PKGWINAPIVWIN32F&ContribRecId=80),
published here so it can be consumed as a library or a package. Check the VDF-GUIdance page for the
original and any newer upstream version.

## What it provides

**Files** — `vCopyFile`, `vMoveFile`, `vRenameFile`, `vDeleteFile`, `vFilePathExists`,
`vConvertFileDateTime`

**Folders** — `vCreateDirectory`, `vshCreateDirectoryEX`, `vRemoveDirectory`, `vFolderExists`,
`vPathIsDirectory`, `vFolderFileCount`

**Temporary and system paths** — `vMakeTempFile`, `vCreateTempFileInPath`, `vGetTempPath`,
`vGetWindowsDirectory`, `vSHGetFolderPath`

**Dialogs** — `vSHBrowseForFolder`, plus `cvFileDialogs.pkg` for the standard file dialogs

## Installing

**DataFlex 26 and later** — add it as a package. Note the path **inside** the repository: the
workspace files live in `StudioLibrary`, and leaving that folder out is what makes an install fail.

```
https://github.com/NilsSve/Library-vwin32fh.git/StudioLibrary/vWin32fh-Library-DF26.0.sws
```

**Earlier DataFlex** — add the matching `.sws` from `StudioLibrary` as a library in your workspace.

## Using it

`Use` the entry point and call the functions:

```dataflex
Use vWin32fh.pkg

If (vFilePathExists(sSource)) ;
    Move (vCopyFile(sSource, sTarget, False)) to bOk
```

⚠️ **`vWin32fh.pkg` is the only file you should `Use`.** It selects between `vwin32fhA.pkg` (ANSI)
and `vwin32fhW.pkg` (Unicode) for your DataFlex version. Using either of those directly — or both —
defeats that choice and produces colliding definitions.

`FileHandlingDemo.src` is a working example that exercises the package.

## Requirements

Windows, and a DataFlex version with a matching `.sws` in `StudioLibrary`. vwin32fh depends on no
other library.

---

## From the original readme

> My apologies for using Visual DataFlex Libraries in a very unconventional way.
>
> For a minimum class library the standard file layout is a bit overkill. Usually there are no data
> files, no IdeSrc required, no bitmaps etc. — just a few packages.
>
> By putting the library meta data files in a subfolder and having the packages at the top, the
> focus stays on the code.
>
> When adding the packages as a library, just select the .sws file version that is for your
> DataFlex version and it should all work as normal. You can find the .sws files in the
> StudioLibrary folder (as is the other meta data stuff).
