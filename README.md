# Apple Leaf Check

Apple leaf disease check that runs entirely in the phone browser. Open the page, take a photo of one apple leaf (or pick a sample), and the model names the disease: apple scab, black rot (frogeye leaf spot), cedar apple rust, or healthy. No image leaves the device.

**Live page:** https://markoamalak.github.io/apple-leaf-check/

## Model
- MobileNetV2 (2.39 M parameters), first trained on the leakage-free PlantVillage apple split, then fine-tuned on PlantVillage + FGVC8 + PlantDoc field training images.
- Exported to ONNX and run with ONNX Runtime Web (WebAssembly, one thread).
- Accuracy on images never used in training: PlantVillage test 100.0% (490 images), FGVC8 field 96.8% (1,200), PlantDoc field 87.9% (58, three classes).
- A simple leaf-tissue check refuses photos that do not look like a leaf. It cannot tell an apple leaf from the leaf of another plant.

Part of the MSc thesis *Detection and Classification of Apple Diseases Using Machine Learning Techniques*, Marko Alkes Malak, Fayoum University. Code and experiments: https://github.com/MarkoAMalak/apple-leaf-disease-framework

## Third-party
`ort.wasm.min.js`, `ort-wasm.wasm` and `ort-wasm-simd.wasm` are from ONNX Runtime Web 1.17.3 (MIT License, Copyright (c) Microsoft Corporation).
