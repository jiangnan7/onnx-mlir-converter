# onnx-mlir-converter

A fork of [onnx-mlir](https://github.com/onnx/onnx-mlir) focused on lowering selected **ONNX dialect** ops to the MLIR **Linalg/Tensor/Arith dialect**.

## Currently Supported Lowerings

| ONNX Dialect Op | Lowered to Linalg/Tensor/Arith |
| :-------------: | :---------------: |
|    onnx.Gemm    |         ✅         |
|   onnx.MatMul   |         ✅         |
|  onnx.Constant  |         ✅         |
|   onnx.Reshape  |         ✅         |
|   onnx.Squeeze  |         ✅         |
|  onnx.Transpose |         ✅         |

More ops will be added in future releases.

## Usage

```sh
./onnx-mlir-opt model.onnx --convert-onnx-to-linalg
```

The output will be an MLIR file using built-in dialect ops, ready for further standard MLIR optimization and lowering.

