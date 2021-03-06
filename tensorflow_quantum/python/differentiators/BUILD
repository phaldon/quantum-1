package(default_visibility = ["//visibility:public"])

licenses(["notice"])

# Export for the PIP package.
exports_files(["__init__.py"])

py_library(
    name = "adjoint",
    srcs = ["adjoint.py"],
    deps = [
        ":differentiator",
        "//tensorflow_quantum/core/ops:tfq_adj_grad_op_py",
    ],
)

py_test(
    name = "adjoint_test",
    srcs = ["adjoint_test.py"],
    deps = [
        ":adjoint",
        "//tensorflow_quantum/core/ops:circuit_execution_ops",
    ],
)


py_library(
    name = "differentiator",
    srcs = ["differentiator.py"],
)

py_library(
    name = "linear_combination",
    srcs = ["linear_combination.py"],
    deps = [
        ":differentiator",
    ],
)

py_library(
    name = "parameter_shift",
    srcs = ["parameter_shift.py"],
    deps = [
        ":differentiator",
        ":parameter_shift_util",
    ],
)

py_library(
    name = "parameter_shift_util",
    srcs = ["parameter_shift_util.py"],
    deps = [
        "//tensorflow_quantum/core/ops:tfq_ps_util_ops_py",
    ],
)

py_test(
    name = "differentiator_test",
    srcs = ["differentiator_test.py"],
    python_version = "PY3",
    deps = [
        ":differentiator",
    ],
)

py_test(
    name = "linear_combination_test",
    srcs = ["linear_combination_test.py"],
    python_version = "PY3",
    deps = [
        ":linear_combination",
        "//tensorflow_quantum/core/ops:circuit_execution_ops",
        "//tensorflow_quantum/python:util",
    ],
)

py_test(
    name = "parameter_shift_test",
    timeout = "long",
    srcs = ["parameter_shift_test.py"],
    python_version = "PY3",
    deps = [
        ":parameter_shift",
        "//tensorflow_quantum/core/ops:circuit_execution_ops",
        "//tensorflow_quantum/core/ops:tfq_utility_ops_py",
        "//tensorflow_quantum/python:util",
    ],
)

py_test(
    name = "parameter_shift_util_test",
    srcs = ["parameter_shift_util_test.py"],
    python_version = "PY3",
    deps = [
        ":parameter_shift_util",
        "//tensorflow_quantum/python:util",
    ],
)

py_test(
    name = "gradient_test",
    timeout = "eternal",
    srcs = ["gradient_test.py"],
    python_version = "PY3",
    deps = [
        ":adjoint",
        ":linear_combination",
        ":parameter_shift",
        "//tensorflow_quantum/core/ops:batch_util",
        "//tensorflow_quantum/core/ops:circuit_execution_ops",
        "//tensorflow_quantum/python:util",
    ],
)
