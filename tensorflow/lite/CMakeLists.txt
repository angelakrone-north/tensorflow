cmake_minimum_required(VERSION 3.13)

SET(CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/../../contrib/cmake")

project(tensorflow-lite)

set(CMAKE_CXX_STANDARD 14)

set(TENSORFLOW_LITE_SOURCES
    allocation.cc
    arena_planner.cc
    graph_info.cc
    interpreter.cc
    kernels/activations.cc
    kernels/add.cc
    kernels/basic_rnn.cc
    kernels/batch_to_space_nd.cc
    kernels/bidirectional_sequence_lstm.cc
    kernels/bidirectional_sequence_rnn.cc
    kernels/concatenation.cc
    kernels/conv.cc
    kernels/depthwise_conv.cc
    kernels/div.cc
    kernels/embedding_lookup_sparse.cc
    kernels/embedding_lookup.cc
    kernels/exp.cc
    kernels/fully_connected.cc
    kernels/gather.cc
    kernels/gemmlowp_support.cc
    kernels/hashtable_lookup.cc
    kernels/internal/kernel_utils.cc
    kernels/internal/optimized/neon_tensor_utils.cc
    kernels/internal/quantization_util.cc
    kernels/internal/reference/portable_tensor_utils.cc
    kernels/internal/tensor_utils.cc
    kernels/kernel_util.cc
    kernels/l2norm.cc
    kernels/local_response_norm.cc
    kernels/lsh_projection.cc
    kernels/lstm.cc
    kernels/mul.cc
    kernels/pad.cc
    kernels/pooling.cc
    kernels/register.cc
    kernels/reshape.cc
    kernels/resize_bilinear.cc
    kernels/skip_gram.cc
    kernels/space_to_batch_nd.cc
    kernels/space_to_depth.cc
    kernels/split.cc
    kernels/squeeze.cc
    kernels/strided_slice.cc
    kernels/sub.cc
    kernels/svdf.cc
    kernels/topk_v2.cc
    kernels/transpose.cc
    kernels/unidirectional_sequence_lstm.cc
    kernels/unidirectional_sequence_rnn.cc
    model.cc
    optional_debug_tools.cc
    simple_memory_arena.cc
    string_util.cc
)

add_library(tensorflow-lite STATIC ${TENSORFLOW_LITE_SOURCES})

target_include_directories(tensorflow-lite
    PUBLIC ../../
    PUBLIC tools/make/downloads/flatbuffers/include
    PRIVATE tools/make/downloads
    PRIVATE tools/make/downloads/eigen
    PRIVATE tools/make/downloads/gemmlowp
    PRIVATE tools/make/downloads/neon_2_sse
    PRIVATE tools/make/downloads/farmhash/src
    PRIVATE gen/obj
)
