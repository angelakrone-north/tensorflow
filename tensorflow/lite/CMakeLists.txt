cmake_minimum_required(VERSION 3.13)

SET(CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/../../contrib/cmake")

project(tensorflow-lite)

set(CMAKE_CXX_STANDARD 14)

set(TENSORFLOW_LITE_SOURCES
    allocation.cc
    arena_planner.cc
    c/c_api_internal.c
    core/subgraph.cc
    core/api/error_reporter.cc
    core/api/flatbuffer_conversions.cc
    core/api/op_resolver.cc
    delegates/nnapi/nnapi_delegate.cc
    experimental/ruy/allocator.cc
    experimental/ruy/block_map.cc
    experimental/ruy/blocking_counter.cc
    experimental/ruy/context.cc
    experimental/ruy/detect_dotprod.cc
    experimental/ruy/kernel.cc
    experimental/ruy/pack.cc
    experimental/ruy/thread_pool.cc
    experimental/ruy/trace.cc
    experimental/ruy/trmul.cc
    experimental/ruy/tune.cc
    graph_info.cc
    interpreter.cc
    kernels/activations.cc
    kernels/add.cc
    kernels/add_n.cc
    kernels/arg_min_max.cc
    kernels/audio_spectrogram.cc
    kernels/basic_rnn.cc
    kernels/batch_to_space_nd.cc
    kernels/bidirectional_sequence_lstm.cc
    kernels/bidirectional_sequence_rnn.cc
    kernels/cast.cc
    kernels/ceil.cc
    kernels/comparisons.cc
    kernels/concatenation.cc
    kernels/conv.cc
    kernels/cpu_backend_context.cc
    kernels/cpu_backend_gemm_eigen.cc
    kernels/cpu_backend_support.cc
    kernels/depthwise_conv.cc
    kernels/dequantize.cc
    kernels/detection_postprocess.cc
    kernels/div.cc
    kernels/eigen_support.cc
    kernels/elementwise.cc
    kernels/embedding_lookup.cc
    kernels/embedding_lookup_sparse.cc
    kernels/exp.cc
    kernels/expand_dims.cc
    kernels/fake_quant.cc
    kernels/fill.cc
    kernels/floor.cc
    kernels/floor_div.cc
    kernels/floor_mod.cc
    kernels/fully_connected.cc
    kernels/gather.cc
    kernels/gather_nd.cc
    kernels/hashtable_lookup.cc
    kernels/if.cc
    kernels/internal/kernel_utils.cc
    kernels/internal/mfcc.cc
    kernels/internal/mfcc_dct.cc
    kernels/internal/mfcc_mel_filterbank.cc
    kernels/internal/spectrogram.cc
    kernels/internal/tensor_utils.cc
    kernels/internal/test_util.cc
    kernels/internal/quantization_util.cc
    kernels/internal/reference/portable_tensor_utils.cc
    kernels/internal/optimized/neon_tensor_utils.cc
    kernels/kernel_util.cc
    kernels/l2norm.cc
    kernels/local_response_norm.cc
    kernels/logical.cc
    kernels/lsh_projection.cc
    kernels/lstm.cc
    kernels/lstm_eval.cc
    kernels/matrix_diag.cc
    kernels/matrix_set_diag.cc
    kernels/maximum_minimum.cc
    kernels/mfcc.cc
    kernels/mirror_pad.cc
    kernels/mul.cc
    kernels/neg.cc
    kernels/one_hot.cc
    kernels/pack.cc
    kernels/pad.cc
    kernels/pooling.cc
    kernels/pow.cc
    kernels/quantize.cc
    kernels/range.cc
    kernels/rank.cc
    kernels/reduce.cc
    kernels/register_ref.cc
    kernels/register.cc
    kernels/reshape.cc
    kernels/resize_bilinear.cc
    kernels/resize_nearest_neighbor.cc
    kernels/reverse.cc
    kernels/reverse_sequence.cc
    kernels/round.cc
    kernels/select.cc
    kernels/shape.cc
    kernels/skip_gram.cc
    kernels/slice.cc
    kernels/space_to_batch_nd.cc
    kernels/space_to_depth.cc
    kernels/sparse_to_dense.cc
    kernels/split.cc
    kernels/split_v.cc
    kernels/squared_difference.cc
    kernels/squeeze.cc
    kernels/strided_slice.cc
    kernels/sub.cc
    kernels/svdf.cc
    kernels/tile.cc
    kernels/topk_v2.cc
    kernels/transpose.cc
    kernels/transpose_conv.cc
    kernels/unidirectional_sequence_lstm.cc
    kernels/unidirectional_sequence_rnn.cc
    kernels/unique.cc
    kernels/unpack.cc
    kernels/where.cc
    kernels/while.cc
    kernels/zeros_like.cc
    minimal_logging.cc
    minimal_logging_default.cc
    mmap_allocation.cc
    model.cc
    mutable_op_resolver.cc
    nnapi/nnapi_implementation.cc
    optional_debug_tools.cc
    simple_memory_arena.cc
    stderr_reporter.cc
    string_util.cc
    util.cc

    tools/make/downloads/farmhash/src/farmhash.cc
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
