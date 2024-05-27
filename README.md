# Collection of Ash Examples

This is a collection of [Vulkan®](https://www.khronos.org/vulkan/) examples created with [Ash](https://github.com/ash-rs/ash) as its wrapper API.

Each example exists in a separate submodule. You can clone all examples with `git clone --recurse-submodules https://github.com/ZakStar17/ash-examples-index` or clone and initialize submodules individually with `git submodule init <path>`.

Each example has its own `README.md` that explains the general code flow, used Vulkan functionality and some differences/similarities to other examples.

Feel free to suggest new examples or improvements for old ones.

## Table of Contents

- [Instance creation](https://github.com/ZakStar17/ash-examples/tree/c0d5371d509978f9baa0b36de90619da94a1660b) (/instance): Covers Instance creation and enabling validation layers.
- [Device creation](https://github.com/ZakStar17/ash-examples/tree/8613bf6d393cf340737d610455c4cf642e8dcc00) (/device): Covers physical device selection, logical device creation and queue retrieval.
- [Compute image clear](https://github.com/ZakStar17/ash-examples/tree/83fdef88739788ea41c504b455045a90c10ccc7f) (/clear_image): Clears an image, copies it from device memory to host accessible (CPU) memory and saves it to a file. This example covers command buffer and image creation, image layout transitions with image barriers, queue family ownership transfer and queue submission.
- [Storage image compute shader](https://github.com/ZakStar17/ash-examples/tree/8cfa06118f1557815d57e873ade3cc322b2cbc17) (/mandelbrot): Generates the Mandelbrot Set offline by using a compute shader on a storage image and saves it to a file. This example covers compute pipeline creation, pipeline caches, descriptor sets and compute shaders. It also demonstrates the use of specialization constants in order to assign constant values in the shader during pipeline creation.
- [Triangle image](https://github.com/ZakStar17/ash-examples/tree/1a780d3456bcb7d6c9796ba2a2735110299f2a8b) (/triangle_image): Draws a triangle and saves it to a file. Covers executing a simple graphics pipeline with a render pass, vertex and index buffers.
- [Bouncing texture](https://github.com/ZakStar17/ash-examples/tree/fc2d9e10ad962c86f9b09056da6c4f9d787126fa) (/bouncy_ferris): Have Ferris the crab bouncing around the screen. Applies a texture to an image and draws it rapidly with different positions. Introduces rendering to windows with a swapchain as well as sampling images.

This list is mostly ordered in terms of difficulty.

## Running

Running the examples requires the nightly Rust Toolchain (`rustup default nightly`) as well as the [Vulkan SDK](https://www.lunarg.com/vulkan-sdk/).

To run a example with all validations enabled, navigate to the respective folder and run `RUST_LOG=debug cargo run <name_of_the_example>`. More information can be found in the respective README.

The examples use cargo features that enable specific functionality. These include `vl` to enable validation layers and `link` or `load` to specify how the Vulkan library is loaded.

The validation layers are enabled by default, which may cause the program to fail if they are not installed. To disable them, disable the `vl` cargo feature. For example, `cargo run --release --no-default-features --features link`.

## Checking the logs

Every example uses the [log](https://github.com/rust-lang/log) crate with [env_logger](https://docs.rs/env_logger/latest/env_logger/) as its facade implementation. This means that, for example, the validation layers (if enabled) will only show errors by default.

Different levels of visibility can be changed with the environment variable `RUST_LOG`, so if
for example you want to see all error, warning, info and debug messages, just run the executable preceding
it with `RUST_LOG=debug`. You can find more information at [https://docs.rs/env_logger/0.11.0/env_logger/](https://docs.rs/env_logger/0.11.0/env_logger/).
