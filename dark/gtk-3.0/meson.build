scss_files = files([
    '_colors-public.scss',
    '_colors.scss',
    '_common.scss',
    '_drawing.scss',
    '_gnome-apps.scss',
    '_lightdm-gtk-greeter.scss',
    '_others.scss',
    '_unity.scss',
    '_xfce.scss'
])

install_subdir('assets', install_dir: theme_path / 'gtk-4.0')
install_subdir('apps', install_dir: theme_path / 'gtk-4.0')
install_data('settings.ini', install_dir : theme_path / 'gtk-4.0')

theme_deps += custom_target('gtk4-dark',
                            input: 'gtk-contained.scss',
                            output: 'gtk.css',
                            command: [
                                sassc, sassc_opts, '@INPUT@', '@OUTPUT@'
                            ],
                            depend_files: scss_files,
                            build_by_default: true,
                            install: true,
                            install_dir: join_paths(theme_path, 'gtk-4.0'))

theme_deps += custom_target('gtk4-dark-dark',
                            input: 'gtk-contained-dark.scss',
                            output: 'gtk-dark.css',
                            command: [
                                sassc, sassc_opts, '@INPUT@', '@OUTPUT@'
                            ],
                            depend_files: scss_files,
                            build_by_default: true,
                            install: true,
                            install_dir: join_paths(theme_path, 'gtk-4.0'))

gtk4_light_gresources = gnome.compile_resources('gtk', 'gtk.gresource.xml',
                                                source_dir: meson.source_root() / 'dark' / 'gtk-4.0',
                                                install: true,
                                                gresource_bundle: true,
                                                install_dir: join_paths(theme_path, 'gtk-4.0'))
