project('cpp-base64','cpp', 
        default_options : ['cpp_std=c++14']
      )


cpp_base64_inc = include_directories('include')
cpp_base64_src = ['base64.cpp']

build_dir = meson.build_root()

cpp_flags = ['-std=c++14',
             '-DINSTALL='+build_dir
             ]

cpp_base64_lib = static_library(
  'cpp_base64',
  sources: cpp_base64_src,
  include_directories: cpp_base64_inc,
  cpp_args: cpp_flags)

cpp_base64_dep = declare_dependency(include_directories: cpp_base64_inc, link_with: cpp_base64_lib)

if meson.is_subproject() == false
  test_exe = executable('UnitTest', ['test.cpp', 'base64.cpp'], dependencies: cpp_base64_dep) 
  dir = '@0@'.format(meson.build_root())
  test('Common unit tests', test_exe, workdir : dir)
endif
