# Build Guide: Device-Specific and Generic Versions


## Device-Specific Build

1. Place the appropriate `abl.img` file into the `./images` directory of the project.

2. Run the build command:

   ```bash
   make build
   ```


## Generic Build

Build a generic version that is not tied to a specific device:

```bash
make build_generic
```


> Note:  
> - The device-specific build requires the corresponding `abl.img` to ensure compatibility.  
> - The generic build works for multiple devices but may have compatibility or performance trade-offs.
