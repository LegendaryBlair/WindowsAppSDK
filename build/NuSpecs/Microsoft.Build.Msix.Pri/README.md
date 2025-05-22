# Microsoft.Build.Msix.Pri Telemetry Disabler

This directory contains targets files to disable telemetry for MakePri.exe during Windows App SDK package builds.

## DisableTelemetry.targets

This file sets environment variables and MSBuild properties to disable telemetry in MakePri.exe, preventing errors related to missing Microsoft.VisualStudio.Utilities.Internal assembly when updating the Windows App SDK NuGet package.

The issue occurs when MakePri.exe attempts to use Visual Studio's telemetry functionality but can't find the required assembly, causing the build to fail with:
```
error MSB6003: The specified task executable "MakePri.exe" could not be run. System.IO.FileNotFoundException: Could not load file or assembly 'Microsoft.VisualStudio.Utilities.Internal, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies. The system cannot find the file specified.
```

This targets file provides a solution by disabling the telemetry feature in MakePri.exe, allowing the build to proceed without requiring the missing assembly.