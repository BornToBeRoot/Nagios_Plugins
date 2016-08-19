# Windows NRPE / NSClient++ debug mode

Stop the NSClient++ service on the Windows server where you want to test the check:

```powershell
Get-Service NSCP | Stop-Service
```

Now start the NSClient++ in debug mode with the parameter `test`:

```powershell
cd "C:\Program Files\NSClient++\"
nscp.exe test
```

Then connect via SSH to your linux server where nagios is running and execute the following command:

```
/usr/lib/nagios/plugins/plugins_app/check_nrpe -H XXX.XXX.XXX.XXX -t 30 -C check_name_XXXX
```

If you are done testing... don't forget to start the NSClient++ service on your Windows server again:

```powershell
Get-Service NSCP | Start-Service
```