Notes for future me:

This is a fork of https://github.com/ceifa/steamworks.js

Override steamworks.js with a custom-built linux64 binary file so that it runs on OpenSuse OS.
By default, the binary is compiled with ubuntu-latest which uses a glibc version that is too new.
This binary has been re-compiled with glibc v2.31

Steps:
- I installed a VM with OpenSuse (glibc 2.31, rust, dev-tools)
- I built the steamworks.js project binary's /linux64 files
- I copied those files and created a repo with an npm dep of steamworks.js (i.e. this repo)
- I published a npm package from the exact steamworks.js source, but added a build step to copy the compiled binary over the default one
- I published the package and used this npm dep instead of the original steamworks.js in my project

Structure
```
/override_files
/libs <---- compiled bin go here
/files <---- package.json (required to change name and version) and updated readme here
```

To push an updated version:
- Update `override_files/files/package.json version`.
- Run `npm run build`
- Run `npm publish` to push new package
- Update consuming repo to use the new version
