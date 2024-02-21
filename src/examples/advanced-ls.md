# Advanced LS


Lists the aboslute path of all files in the given path.


```blade
import os

var path = os.args.length() > 2 ? os.args[2] : '.'
var files = os.read_dir(path)
var dir = os.real_path(path)

for f in files {
  if f echo '${dir}${os.path_separator}${f}'
}
```
