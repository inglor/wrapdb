project('fmt', 'cpp',
    version : '9.0.0',
    license : 'BSD',
    default_options : ['cpp_std=c++14']
)

fmt_private_cpp_args = [ ]
fmt_interface_cpp_args = [ ]
libtype = get_option('default_library')
if libtype == 'shared'
    fmt_private_cpp_args += [ '-DFMT_EXPORT' ]
    fmt_interface_cpp_args += [ '-DFMT_SHARED' ]
endif

fmt_inc = include_directories('include')
fmt_lib = library('fmt',
    sources : [
        'src/format.cc',
        'src/os.cc'
    ],
    cpp_args : fmt_private_cpp_args,
    include_directories : fmt_inc
)

fmt_dep = declare_dependency(
    include_directories : fmt_inc,
    compile_args : fmt_interface_cpp_args,
    link_with : fmt_lib
)

if meson.version().version_compare('>=0.54.0')
  meson.override_dependency('fmt', fmt_dep)
endif

fmt_header_only_dep = declare_dependency(
    include_directories : fmt_inc,
    compile_args : '-DFMT_HEADER_ONLY'
)
