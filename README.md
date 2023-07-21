# vpphelper

vpphelper provides helper functions (using govpp) that helps to connect to VPP and configure VPP using a configuration (.conf) file.

`StartAndDialContext` function starts VPP using a VPP configuration file and returns a `Connection` to VPP.

```go
conn, vppErrCh := vpphelper.StartAndDialContext(connectCtx)
``` 
The following two functional options can also be passed as parameters to the `StartAndDialContext` function:  
1. `WithRootDir` : sets the root directory for all `.conf` files
2. `WithVppConfig` : sets `vpp.conf` file template. All the `%[1]s` in the template will be replaced by the `rootDir`.
```go
conn, vppErrCh := vpphelper.StartAndDialContext(connectCtx, vpphelper.WithRootDir("/tmp/vpp2"), vpphelper.WithVppConfig(newDefaultVPPConfTemplate))
```
		
**Note**: `newDefaultVPPConfTemplate` variable in above code snippet is a multiline string having `vpp.conf` template. An example of such template is available in `vpp.conf.go`.
