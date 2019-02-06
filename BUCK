load('//:subdir_glob.bzl', 'subdir_glob')
load('//:buckaroo_macros.bzl', 'buckaroo_deps', 'buckaroo_deps_from_package')

boost_test = buckaroo_deps_from_package('github.com/buckaroo-pm/boost-test')

# Some tests and examples use files from include_private
prebuilt_cxx_library(
  name = 'math-private',
  header_namespace = '',
  header_only = True,
  exported_headers = subdir_glob([
    ('include_private', '**/*.hpp'),
  ]),
  visibility = [
    'PUBLIC',
  ],
)

cxx_library(
  name = 'math',
  header_namespace = '',
  exported_headers = subdir_glob([
    ('include', '**/*.hpp'),
    ('include', '**/*.ipp'),
  ]),
  headers = subdir_glob([
    ('include_private', '**/*.hpp'),
    ('src/tr1', '**/*.hpp'),
  ]),
  srcs = glob([
    'src/**/*.cpp',
  ]),
  deps = [ x for x in buckaroo_deps() if not x in boost_test ],
  visibility = [
    'PUBLIC',
  ],
)
