I installed a VM with OpenSuse
I built the steamworks.js project binary's /linux64 files
I copied those files and created a repo with a dep of steamworks.js
I published a npm package from the exact steamworks.js source, but added a build step to copy the compiled binary over the default one
I published the package and used this npm dep instead of the original steamworks.js

/override_files
    /libs <---- compiled bin go here
    /files <---- package.json (required to change name and version) and updated readme here

Run `npm run build` to publish another version