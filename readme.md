# themeswap

A quick and dirty application for swapping themes with .json configuration files and jinja template files.

## installation

Clone the repository and install jinja2.

```bash
git clone https://github.com/paracorde/themeswap.git
pip install --user jinja2
```

## configuration

The script will search for the config file at `~/.config/themes/config.json`. An alternate path can be supplied with the `--config` option. (Or you could just modify the script itself.)

The `config.json` file should have be in the style below:

```json
{
  "generate": {
    "/file/path/to/template": "/file/path/to/destination",
    ...
  },
  "commands": [
    "do some stuff",
    "do more stuff",
    ... commands to run here ...
  ]
}
```

The theme directory will be (by default) `~/.config/themes/documents/`. Each theme file should be a .json file. An example of a theme is shown below:

```json
{
  "name": "theme_name",
  "author": "author_name",
  "color": [
    ... colors 0-15 as strings here...
  ],
  "foreground": "#______",
  "background": "#______",
  "opacity": 0.0 - 1.0,
  ... extra data as needed ...
}
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
