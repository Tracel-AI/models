# ResNet Burn

To this day, [ResNet](https://arxiv.org/abs/1512.03385)s are still a strong baseline for your image
classification tasks. You can find the [Burn](https://github.com/tracel-ai/burn) implementation for
the ResNet variants in [src/model/resnet.rs](src/model/resnet.rs).

The model is [no_std compatible](https://docs.rust-embedded.org/book/intro/no-std.html).

## Usage

### `Cargo.toml`

Add this to your `Cargo.toml`:

```toml
[dependencies]
resnet-burn = { git = "https://github.com/burn-rs/models", package = "resnet-burn", default-features = false }
```

If you want to get the pre-trained ImageNet weights, enable the `pretrained` feature flag.

```toml
[dependencies]
resnet-burn = { git = "https://github.com/burn-rs/models", package = "resnet-burn", features = ["pretrained"] }
```

**Important:** this feature requires `std`.

### Example Usage

The [inference example](examples/inference.rs) initializes a ResNet-18 from the ImageNet
[pre-trained weights](https://pytorch.org/vision/stable/models/generated/torchvision.models.resnet18.html#torchvision.models.ResNet18_Weights)
with the `NdArray` backend and performs inference on the provided input image.

You can run the example with the following command:

```sh
cargo run --release --features pretrained --example inference samples/dog.jpg
```
