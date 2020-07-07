# themeswap

A quick and dirty application for swapping themes with .toml configuration files and jinja template files.

## installation

Clone the repository and install jinja2.

```bash
git clone https://github.com/paracorde/themeswap.git
pip install --user jinja2
```

## configuration

The script will search for the config file at `~/.config/themes/config.toml`. An alternate path can be supplied with the `--config` option. (Or you could just modify the script itself.)

The `config.toml` file should be in the style below:

```toml
[general]
# theme_path = "~/.config/themes/documents"
# script = "bash ~/.config/bin/themeswap"

[generate]
"/path/to/template" = "path/to/destination"
...
```

The theme directory will be (by default) `~/.config/themes/documents/`. Each theme file should be a .toml file. An example of a theme is shown below:

```toml
[general]
name = "theme_name"
author = "author_name"
# script = "bash ~/.config/bin/themeswap"

[style]
color = [
  "#______",
  "#______",
  "#______",
  "#______",
  "#______",
  "#______",
  "#______",
  "#______",
  "#______",
  "#______",
  "#______",
  "#______",
  "#______",
  "#______",
  "#______",
  "#______"
]
foreground = "#______"
background = "#______"
opacity = 1.0
# additional settings you want template files to be able to access:
# wallpaper = "~/.config/themes/wallpapers/fairylights.jpg"

```

Template files just use the jinja2 syntax. Here would be a template file for a .Xresources file:

```
*.foreground: {{ foreground }}
*.background: {{ background }}
*.color0: {{ color[0] }}
*.color8: {{ color[8] }}
*.color1: {{ color[1] }}
*.color9: {{ color[9] }}
*.color2: {{ color[2] }}
*.color10: {{ color[10] }}
*.color3: {{ color[3] }}
*.color11: {{ color[11] }}
*.color4: {{ color[4] }}
*.color12: {{ color[12] }}
*.color5: {{ color[5] }}
*.color13: {{ color[13] }}
*.color6: {{ color[6] }}
*.color14: {{ color[14] }}
*.color7: {{ color[7] }}
*.color15: {{ color[15] }}
```

The `script` under the general section of `config.toml` or the theme file will also be run, with the theme file taking higher precedence if both are defined.

For example, you can set the `wallpaper` attribute under `[style]` and generate this script with a template, so that the script can set the wallpaper for the theme.
