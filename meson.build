project(
  'python-siphash24', 'c', 'cython',
  license: 'GPL-3',
  meson_version: '>= 1.0.0',
  default_options: [
    'buildtype=release',
    'c_std=c11',
  ]
)

libcsiphash = dependency('libcsiphash-1', version: '>= 1.1.0', static: true)

py = import('python').find_installation()

tempita = files('tempita.py')

pyx = custom_target(
  'siphash24.pyx',
  input: 'siphash24.pyx.in',
  output: 'siphash24.pyx',
  command: [py, tempita, '@INPUT@', '@OUTPUT@']
)

py.extension_module(
  'siphash24',
  pyx,
  dependencies: libcsiphash,
  install: true
)
