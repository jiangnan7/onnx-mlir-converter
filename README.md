<!--- SPDX-License-Identifier: Apache-2.0 -->
<p align="center"><img width="50%" src="docs/logo/onnx-mlir-1280x640.png" /></p>

# onnx-mlir-converter

A fork of [onnx-mlir](https://github.com/onnx/onnx-mlir) focused on lowering selected **ONNX dialect** ops to the MLIR **Linalg/Tensor/Arith dialect**.

## Currently Supported Lowerings

### Math Ops
| ONNX Dialect Op |  Lowered to  Linalg/Tensor/Arith|
| :-------------: | :----------: |
|   `ONNXGemmOp`   | ✅ |
|  `ONNXMatMulOp`  | ✅ |
|  `ONNXClipOp`    | ✅ |
|  `ONNXReluOp`    | ✅ |
|  `ONNXAddOp`     | ✅ |
|  `ONNXSubOp`     | ✅ |
|  `ONNXSigmoidOp` | ✅ |


### Tensor Ops
|  ONNX Dialect Op |   Lowered to Linalg/Tensor/Arith  |
| :--------------: | :----------: |
|  `ONNXConstantOp` | ✅ |
|  `ONNXReshapeOp`  | ✅ |
|  `ONNXSqueezeOp`  | ✅ |
|  `ONNXTransposeOp`| ✅ |
|  `ONNXSliceOp`    | ✅ |
|  `ONNXSplitOp`    | ✅ |

### NN Ops
|  ONNX Dialect Op |   Lowered to Linalg/Tensor/Arith  |
| :--------------: | :----------: |
|  `ONNXAveragePoolOp` | ✅ |
|  `ONNXMaxPoolSingleOutOp`  | ✅ |


More ops will be added in future releases.

## Usage

```sh
./onnx-mlir-opt model.onnx --convert-onnx-to-linalg
```

The output will be an MLIR file using built-in dialect ops, ready for further standard MLIR optimization and lowering.

