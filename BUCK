load('//:subdir_glob.bzl', 'subdir_glob')
load('//:buckaroo_macros.bzl', 'buckaroo_deps')

prebuilt_cxx_library(
  name = 'math-headers',
  header_only = True,
  header_namespace = '',
  exported_headers = subdir_glob([
    ('include', '**/*.hpp'),
  ]),
  visibility = [
    'PUBLIC',
  ],
)

cxx_library(
  name = 'math',
  header_namespace = '',
  headers = subdir_glob([
    ('include_private', '**/*.hpp'),
    ('src/tr1', '**/*.hpp'),
  ]),
  srcs = glob([
    'src/**/*.cpp',
  ]),
  deps = [
    ':math-headers',
  ] + buckaroo_deps(),
  visibility = [
    'PUBLIC',
  ],
)
