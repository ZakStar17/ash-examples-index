# Collection of Ash Examples

This is a collection of [Vulkan®](https://www.khronos.org/vulkan/) examples created with [Ash](https://github.com/ash-rs/ash) as its wrapper API.

This project is intended to be similar to the official [Vulkan Samples](https://github.com/KhronosGroup/Vulkan-Samples), however built in a way more fitting for Rust.

As of now, each example has its own `README.md` that explains explains some of the Vulkan functionality and how it is applied in the context of the example's code. Most of it is meant to be introductory but may be incomplete from a beginner's perspective, so I try to link other sources that may explain the technical parts better.

Each example exists in a separate git submodule. You can clone all examples with `git clone --recurse-submodules https://github.com/ZakStar17/ash-examples-index` or clone and initialize submodules individually with `git submodule init <path>`.

Feel free to suggest new examples or improvements for old ones.

## Table of Contents

- [Instance creation](https://github.com/ZakStar17/ash-examples/tree/9f44420e63370e1fab0ce38cfcf29236be59c6eb) (/instance): Covers Instance creation and using validation layers.
- [Device creation](https://github.com/ZakStar17/ash-examples/tree/d753d511cabf34af16bbddf399526c6269dc6e77) (/device): Covers physical device selection, logical device creation and queue retrieval.
- [Compute image clear](https://github.com/ZakStar17/ash-examples/tree/ae662162e7d80cb64e7eaf03975dbe2e0ad83dc0) (/clear_image): Clears an image, copies it from device memory to host accessible (CPU) memory and saves it to a file. This example covers command buffer and image creation, image layout transitions with image barriers, queue family ownership transfer and queue submission.
- [Storage image compute shader](https://github.com/ZakStar17/ash-examples/tree/306e3cc3b4b4294f496810c148f5a0ca5ade249a) (/mandelbrot): Uses a compute shader to draw the Mandelbrot Set to a image without creating any windows, and then saves that image to a file. This example covers compute pipeline creation, pipeline caches, descriptor sets and compute shaders. It also demonstrates the use of specialization constants in order to assign constant values in the shader during pipeline creation.
- [Triangle image](https://github.com/ZakStar17/ash-examples/tree/16051a978a36cc5797160e5b5249fd4f11572586) (/triangle_image): Draws a triangle to an image without creating any windows and saves that image to a file. Covers executing a simple graphics pipeline with a render pass, vertex and index buffers.
- [Bouncing texture](https://github.com/ZakStar17/ash-examples/tree/0c616e9239c9fb0f12ca437c273990759bd03f5b) (/bouncy_ferris): Have Ferris the crab bouncing around the screen. Applies a texture to an image and draws it each frame at different positions. Introduces rendering to windows with a swapchain as well as sampling images.

## Building and running

Running the examples requires the nightly Rust Toolchain (`rustup default nightly`) as well as the [Vulkan SDK](https://www.lunarg.com/vulkan-sdk/).

Each example uses a set of cargo features that can be enabled or disabled to toggle specific functionality, which you can customize by using the `--features` flag.

To run an example with all validations enabled, navigate to the respective folder and run:

```bash
RUST_LOG=debug cargo run
```

To run an example with validation layers disabled and with optimizations, navigate to the respective folder and run:

```bash
cargo run --release --no-default-features --features link
```

The `link` / `load` features specify if the Vulkan Loader shall be linked at runtime or compile time (see https://docs.vulkan.org/guide/latest/loader.html). `vl` enables the use of validation layers. More information, as well as the list of default cargo features can be found in the respective example's README.

## Checking the logs

Every example uses the [log](https://github.com/rust-lang/log) crate with [env_logger](https://docs.rs/env_logger/latest/env_logger/) as its facade implementation. This means that, for example, the validation layers (if enabled) will only show errors by default.

Different levels of visibility can be changed with the environment variable `RUST_LOG`, so if
for example you want to see all error, warning, info and debug messages, just run the executable preceding
it with `RUST_LOG=debug`. You can find more information at [https://docs.rs/env_logger/0.11.0/env_logger/](https://docs.rs/env_logger/0.11.0/env_logger/).
