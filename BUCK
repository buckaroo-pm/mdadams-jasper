load('//:subdir_glob.bzl', 'subdir_glob')
load('//:buckaroo_macros.bzl', 'buckaroo_deps')

cxx_library(
  name = 'jasper',
  header_namespace = '',
  srcs = glob([
    'src/libjasper/**/*.c'
  ], exclude=['src/libjasper/jpg/jpg_dummy.c']),
  headers = subdir_glob([
    ('src/libjasper', '*/*.h')
  ]),
  exported_headers = dict(
    subdir_glob([
      ('src/libjasper/include', '**/*.h')
    ]).items() + 
      [('jasper/jas_config.h', 'jas_config.h')]),
  visibility = ['PUBLIC'],
  deps = buckaroo_deps()
  )


cxx_binary(
  name = 'imgcmp',
  srcs = ['src/appl/imgcmp.c'],
  deps = [':jasper'],
  visibility = ['PUBLIC']
)
