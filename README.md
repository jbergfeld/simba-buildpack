# simba buildpack

To use this repo on a cloudfoundry instance simply zip it up. Note: The Simba driver depends on the GSSAPI plugin, so use the `apt` buildpack to install the "libsasl2-modules-gssapi-mit" package before use.

Ex:

1) Zip it up
```
# from the root of this repo, zip up buildpack excluding the .git directory 
zip -r simba-buildpack-v1.0.0.zip . -x *.git*
```
2) upload the buildpack to cloudfoundry
```
cf create-buildpack simba_buildpack simba-buildpack-v1.0.0.zip <INDEX>
```
3) push an app
```
cd <app-rootdir>
# note the buildpack created above cannot be the final buildpack
cf push my-app -b simba_buildpack -b <final-buildpack>  
```

