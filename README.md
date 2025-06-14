1. sudo apt remove amdgpu-install
2. sudo apt update

This is the link where I downloaded the amdgpu-install package:
3. wget https://repo.radeon.com/amdgpu-install/6.1.3/ubuntu/jammy/amdgpu-install_6.1.60103-1_all.deb

4. sudo apt install ./amdgpu-install_6.1


To install applications that uses rocm (ie. pytorch, tensorflow, onnxruntime, etc.) you can use the following commands:

5. wget https://repo.radeon.com/rocm/manylinux/rocm-rel-6.1.3/onnxruntime_rocm-1.17.0-cp310-cp310-linux_x86_64.whl
6. wget https://repo.radeon.com/rocm/manylinux/rocm-rel-6.1.3/pytorch_triton_rocm-2.1.0%2Brocm6.1.3.4d510c3a44-cp310-cp310-linux_x86_64.whl
7. wget https://repo.radeon.com/rocm/manylinux/rocm-rel-6.1.3/tensorflow_rocm-2.15.1-cp310-cp310-manylinux_2_28_x86_64.whl
8. wget https://repo.radeon.com/rocm/manylinux/rocm-rel-6.1.3/torch-2.1.2%2Brocm6.1.3-cp310-cp310-linux_x86_64.whl
9. wget https://repo.radeon.com/rocm/manylinux/rocm-rel-6.1.3/torchvision-0.16.1%2Brocm6.1.3-cp310-cp310-linux_x86_64.whl

10. pip install *.whl

11. location=$(pip show torch | grep Location | awk -F ": " '{print $2}')
12. cd ${location}/torch/lib/
13. rm libhsa-runtime64.so*