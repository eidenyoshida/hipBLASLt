# ########################################################################
# Copyright (C) 2022-2023 Advanced Micro Devices, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
# THE SOFTWARE.
#
# ########################################################################

set(hipblaslt_source_common  src/hipblaslt_ostream.cpp)

if(NOT BUILD_CUDA)
  # hipBLASLt source
  include(src/amd_detail/rocblaslt/CMakeLists.txt)
  set(hipblaslt_source src/amd_detail/hipblaslt.cpp
                       src/amd_detail/hipblaslt-ext.cpp
                       src/amd_detail/hipblaslt-ext-op.cpp
                         ${hipblaslt_source_common}
                         ${rocblaslt_source})
else()
  # hipBLASLt CUDA source
  # TODO
  #set(hipblaslt_source src/nvcc_detail/hipblaslt.cpp)
endif()
