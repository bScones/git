wish = find_program('wish', required: get_option('gitk'))
gitk_enabled = wish.found()

if not gitk_enabled
  subdir_done()
endif

custom_target(
  command: [
    shell,
    meson.current_source_dir() / 'generate-tcl.sh',
    wish.full_path(),
    '@INPUT@',
    '@OUTPUT@',
  ],
  input: 'gitk',
  output: 'gitk',
  depend_files: [
    'generate-tcl.sh',
  ],
  env: script_environment,
  install: true,
  install_dir: get_option('bindir'),
)

if intl.found()
  subdir('po')
endif
