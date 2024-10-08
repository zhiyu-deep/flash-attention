project(flash-attention)

enable_language(CUDA CXX)

set(sources
        csrc/flash_attn/flash_api.cpp
        csrc/flash_attn/src/flash_fwd_hdim32_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim32_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim64_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim64_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim96_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim96_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim128_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim128_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim160_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim160_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim192_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim192_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim256_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim256_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim32_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim32_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim64_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim64_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim96_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim96_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim128_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim128_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim160_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim160_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim192_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim192_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim256_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_hdim256_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim32_fp16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim32_bf16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim64_fp16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim64_bf16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim96_fp16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim96_bf16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim128_fp16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim128_bf16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim160_fp16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim160_bf16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim192_fp16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim192_bf16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim256_fp16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim256_bf16_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim32_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim32_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim64_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim64_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim96_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim96_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim128_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim128_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim160_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim160_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim192_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim192_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim256_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_bwd_hdim256_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim32_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim32_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim64_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim64_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim96_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim96_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim128_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim128_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim160_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim160_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim192_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim192_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim256_fp16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim256_bf16_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim32_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim32_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim64_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim64_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim96_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim96_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim128_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim128_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim160_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim160_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim192_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim192_bf16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim256_fp16_causal_sm80.cu
        csrc/flash_attn/src/flash_fwd_split_hdim256_bf16_causal_sm80.cu
        )

set(CMAKE_CXX_FLAGS "-O3 -std=c++17")

add_library(flash_attention SHARED ${sources})
target_include_directories(flash_attention PRIVATE
        csrc/flash_attn
        csrc/flash_attn/src
        csrc/cutlass/include
        /usr/local/lib/python3.8/dist-packages/torch/include
        /usr/local/lib/python3.8/dist-packages/torch/include/torch/csrc/api/include
        /home/jiangzhiyu/evs/cuda_12/targets/x86_64-linux/include)
target_compile_options(flash_attention PRIVATE "-gencode arch=compute_90,code=sm_90")
