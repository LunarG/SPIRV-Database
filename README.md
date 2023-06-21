# SPIRV-Database

This is a collection of Vulkan SPIR-V files for testing.

This was created to allow [SPIRV-Hopper](https://github.com/KhronosGroup/Vulkan-ValidationLayers/tree/main/tests/spirv_hopper) to run against a large number of SPIR-V modules in order to tests the Validation Layer's shader validation. This repo was created so GitHub Actions can pull down these files to tests.

## Contents

All these shaders are from various open source projects. `fdupes` was ran to reduce any duplicates

The extra `vulkan` folder is so `spirv-hopper` doesn't try and run against all the `.git` files

- SaschaWillemsVulkan
    - There are the shaders from https://github.com/SaschaWillems/Vulkan/
    - 240a56e44108d480bb3b01444b26552ba70857cc (5/23/2023)
- clspv
    - These are generated when running the test suite in https://github.com/google/clspv
        - used `ctest` and took output binaries
    - d029301d86ead45a7ff7c67bcc4bc4daaf49d8aa (5/18/2023)
- tint
    - These are from https://github.com/dneto0/spirv-samples/
    - These can be reproduced from running the test suite in https://dawn.googlesource.com/tint
        - About 50 new ones were added from the test suite
        - Added code to test framework to dump to binary when done
- dawn
    - Ran `./out/Release/dawn_end2end_tests --enable-toggles=dump_shaders` and parsed output to create these
    - Ran on 5/23/2023
- naga/remaps
    - These are using [Naga](https://github.com/gfx-rs/naga) to take some of the SPIR-V in this repo as input and re-output it
- gl_cts
    - Used Zink/ANGLE to run shader focused GL CTS tests
    - The following are how the CTS folders are broken up:
    - shaders
        - `*KHR-*.shaders.*`
    - functional/*
        - `*functional.shader*:*functional.ubo*:*functional.compute*:*functional.ssbo*:*functional.image_load_store*:*functional.tessellation*:*functional.geometry*`
    - shader_extra
        - `*shader_atomic_counters*:*core.layout_binding*:*shader_integer_mix*:*shader_storage_buffer_object*:*compute_shader*:*gpu_shader5*:*shading_language_420pack*`
    - shader_gl46
        - `KHR-GL46.shaders30*:KHR-GL46.gpu_shader_fp64*:KHR-GL46.texture_gather*:KHR-GL46.shader_*:KHR-GL46.gl_spirv*`

