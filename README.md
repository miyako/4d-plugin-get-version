# 4d-plugin-get-version
Function to identify the windows version.

Workaround proposal for [PLATFORM PROPERTIES](http://doc.4d.com/4Dv15/4D/15/PLATFORM-PROPERTIES.301-2007515.en.html) which would always return ``6.2`` for version above Windows 8.

See [GetVersionEx](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724451(v=vs.85).aspx) and [Version Helper functions](https://msdn.microsoft.com/en-us/library/windows/desktop/dn424972(v=vs.85).aspx) for detailed explanation.

### Platform

| carbon | cocoa | win32 | win64 |
|:------:|:-----:|:---------:|:---------:|
|||<img src="https://cloud.githubusercontent.com/assets/1725068/22371562/1b091f0a-e4db-11e6-8458-8653954a7cce.png" width="24" height="24" />|<img src="https://cloud.githubusercontent.com/assets/1725068/22371562/1b091f0a-e4db-11e6-8458-8653954a7cce.png" width="24" height="24" />|

### Remarks

```PLATFORM PROPERTIES``` has been updated in v15.0-188681, v14.4-188703 to report Windows 8.1 correctly. (ACI0089966)

## Syntax

```
version:=Windows Get version (option)
```

Parameter|Type|Description
------------|------------|----
option|LONGINT|``GetVersionInfoEx`` or ``GetFileVersionInfo``
version|TEXT|

Passing ```GetVersionInfoEx``` will simply call the corresponding Win32 API; the number will be incorrect for Window 8.1 and 10. Passing ```GetFileVersionInfo```, on the other hand, will report the version number of Kernel32.dll instead.

```
isWOW64:=Windows Is WOW64
```

Parameter|Type|Description
------------|------------|----
isWOW64|LONGINT|
