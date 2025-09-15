# Matplotlib Chinese Fonts Support

1. Locate 'fonts' folder of current python enviroment.

```python
import import matplotlib
print(matplotlib.matplotlib_fname()
>>> /usr/local/lib/python3.10/dist-packages/matplotlib/mpl-data/matplotlibrc
```

Thus the fonts of matplotlib is `/usr/local/lib/python3.10/dist-packages/matplotlib/mpl-data/fonts/ttf`

2. Download the `SimHei.ttf` file, and place it into matplotlib font directory.

```shell
wget https://github.com/ZongwuWang/MatplotlibChineseFonts/raw/refs/heads/master/SimHei.ttf
mv SimHei.ttf /usr/local/lib/python3.10/dist-packages/matplotlib/mpl-data/fonts/ttf
```

3. Delete the cache file of matplotlib

```shell
cd ~/.cache/matplotlib
rm -rf *.*
```

Step 1-3 can be combined with:

```shell
wget -P "$(python3 -c "import os, matplotlib; print(os.path.dirname(matplotlib.matplotlib_fname()) + '/fonts/ttf')")" https://github.com/ZongwuWang/MatplotlibChineseFonts/raw/refs/heads/master/SimHei.ttf && python3 -c "import matplotlib; matplotlib.font_manager._rebuild()"
```

4. Adjust font in your code.

```python
import matplotlib as mpl
from matplotlib import pyplot as plt
mpl.rcParams[u'font.sans-serif'] = ['simhei']
mpl.rcParams['axes.unicode_minus'] = False
```

