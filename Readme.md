How to fix tikzplotlib to work with Matplotlib > 3.7

1. In _axes.py, replace
'''
from matplotlib.backends.backend_pgf import (
    common_texification as mpl_common_texification,
)
'''

by 

'''
from matplotlib.backends.backend_pgf import (
    _tex_escape as mpl_common_texification,
)
'''

2. In _color.py, replace
   '''
    for h, name in webcolors.names("css3"):
        r = int(h[1:3], 16)
        g = int(h[3:5], 16)
        b = int(h[5:7], 16)
   '''

   by
   '''
    for name in webcolors.names("css3"):
        r, g, b = webcolors.name_to_rgb(name)
        # r = int(h[1:3], 16)
        # g = int(h[3:5], 16)
        # b = int(h[5:7], 16)
   '''


