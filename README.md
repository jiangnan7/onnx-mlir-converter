<!--- SPDX-License-Identifier: Apache-2.0 -->
<p align="center"><img width="50%" src="docs/logo/onnx-mlir-1280x640.png" /></p>

# onnx-mlir-converter

A fork of [onnx-mlir](https://github.com/onnx/onnx-mlir) focused on lowering selected **ONNX dialect** ops to the MLIR **Linalg/Tensor/Arith dialect**.

## Currently Supported Lowerings

```
converter/
├── sample/  # Test cases and examples
│   ├── Math/
│   ├── NN/
│   ├── ONNX/
│   └── Tensor/
└── src/    # Source Code
    └── Conversion/
        └── ONNXToLinalg/
            ├── ConvertONNXToLinalg.cpp # Main converter implementation
            ├── Math/
            ├── NN/
            └── Tensor/

```

### Math Ops
| ONNX Dialect Op |  Lowered to  Linalg/Tensor/Arith|
| :-------------: | :----------: |
|   `ONNXGemmOp`   | ✅ |
|  `ONNXMatMulOp`  | ✅ |
|  `ONNXClipOp`    | ✅ |
|  `ONNXSoftmaxOp1`   | ✅ |
|  `ONNXSoftmaxOpV11Op`   | ✅ |
|  `ONNXReduceSumOp`   | ✅ |
|  `ONNXReduceMaxOp`   | ✅ |
|  `ONNXReduceMinOp`   | ✅ |

Due to limitations in `linalg::ReduceOp`, ONNXReduceOp currently only support reduction over only a single axis. `ONNXSoftMaxOp` and `ONNXSoftmaxV11Op` supports generating multiple ONNXReduceSumOps to perform consecutive reductions from the specified axis to the last dimension.


| ONNX Dialect Op |  Lowered to  Linalg/Tensor/Arith|
| :-------------: | :----------: |
|  `ONNXReluOp`    | ✅ |
|  `ONNXAddOp`     | ✅ |
|  `ONNXSubOp`     | ✅ |
|  `ONNXAbsOp`     | ✅ |
|  `ONNXSigmoidOp` | ✅ |
|  `ONNXMulOp`     | ✅ |
|  `ONNXDivOp`     | ✅ |
|  `ONNXLogOp`     | ✅ |
|  `ONNXExpOp`     | ✅ |
|  `ONNXTanhOp`    | ✅ |
|  `ONNXMaxOp`     | ✅ |
|  `ONNXMinOp`     | ✅ |
|  `ONNXCeilOp`    | ✅ |
|  `ONNXPowOp`     | ✅ |
|  `ONNXAndOp`     | ✅ |
|  `ONNXFloorOp`   | ✅ |
|  `ONNXSinOp`     | ✅ |
|  `ONNXCosOp`     | ✅ |


### Tensor Ops
|  ONNX Dialect Op |   Lowered to Linalg/Tensor/Arith  |
| :--------------: | :----------: |
|  `ONNXConstantOp` | ✅ |
|  `ONNXReshapeOp`  | ✅ |
|  `ONNXSqueezeOp`  | ✅ |
|  `ONNXTransposeOp`| ✅ | 
|  `ONNXSliceOp`    | ✅ |
|  `ONNXPadOp`      | ✅ |
|  `ONNXConcatOp`   | ✅ |
|  `ONNXSplitOp`    | ✅ |
|  `ONNXArgMaxOp`   | ✅ |
|  `ONNXDimOp`   | ✅ | 
|  `ONNXGatherOp`   | ✅ |
 

### NN Ops
|  ONNX Dialect Op |   Lowered to Linalg/Tensor/Arith  |
| :--------------: | :----------: |
|  `ONNXAveragePoolOp` | ✅ |
|  `ONNXMaxPoolSingleOutOp`  | ✅ |


More ops will be added in future releases.

## Usage

```sh
./build/Release/bin/onnx-mlir-opt model.onnx.mlir --convert-onnx-to-linalg
```

The output will be an MLIR file using built-in dialect ops, ready for further standard MLIR optimization and lowering. 

If needed, please contact me at jnli22@m.fudan.edu.cn, and I will provide you with the executable file.
