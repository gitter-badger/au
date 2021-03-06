# Development

The development requires Powershell 5+.

The following scripts are used during development and deployment:

- `setup.ps1`  
Install dependencies for everything.
- `build.ps1`  
Build the module and packages.
- `install.ps1`  
Install the module in the system.
- `publish.ps1`  
Publish module to Powershell Gallery, Chocolatey and Github.


## Build and test

The builded module will be available in the `_build\{version}` directory. Version is by default determined automatically based on the current time.

```
./build.ps1
```

To override default versions use `Version` parameter: `./build -Version 0.0.1`. To build and install in the system use `./build.ps1 -Install`.

Run `Invoke-Pester` in the root to run [Pester](https://github.com/pester/Pester) tests.

To clean temporary files run `git clean -Xdf`.  **However, keep in mind that other unversioned files will be deleted.**


## Publish

The `publish.ps1` script publishes to Github, PSGallery and Chocolatey. There is a switch parameter for each publishing platform:

```
./publish.ps1 -Github -PSGallery -Chocolatey
```

Before publishing, edit the `NEXT` header in the `CHANGELOG.md` file to set the release notes and build the module. The publish script will take first second level header after the `NEXT` (the latest version) as release notes.

Publishing procedure depends on number of environment variables. Rename `vars_default.ps1` to `vars.ps1` and set variables there to get them included.


