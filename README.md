# Fix Winget Not loading

If your winget version is out of date, then it may be stuck like this:

![image](https://johan-cho.github.io/src/img/WINGET_STUCK.png)

This script tries to reinstall winget.

## Running

```powershell
(invoke-webrequest https://raw.githubusercontent.com/johan-cho/winget-fix/master/winget-fix.ps1).content | powershell
```

This script tries to install winget from the offical repository, which may fail because of a dependency on [`Microsoft.XAML.UI`](https://github.com/microsoft/microsoft-ui-xaml).

```traceback
Add-AppxPackage : Deployment failed with HRESULT: 0x80073CF3, Package failed updates, dependency or conflict validation. Windows cannot install package Microsoft.DesktopAppInstaller_1.22.10582.0_x64__8wekyb3d8bbwe because this package depends on a framework that could not be found. Provide the framework "Microsoft.UI.Xaml.2.8" published by "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US", with neutral or x64 processor
```

This script then tries to install XAML.UI and then go back to reinstalling winget. If you're only getting the last error, you could try to just use the `Install-MSXML` function in the script.
