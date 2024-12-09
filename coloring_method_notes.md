# Notes on Categorical Coloring Method

**Purpose:**  
For future mapping and data visualization projects where multiple categories (e.g., ~30) need distinct and visually separable colors, we use a combination of `matplotlib`'s qualitative colormaps (`tab20`, `tab20b`, `tab20c`).

**Method Used:**  
- Import `matplotlib` colormaps.
- Extract colors from `tab20`, `tab20b`, and `tab20c` to get a large pool (~60 colors).
- Use the first `n` colors from this combined list.
- Assign each category a unique color from this pool.

**Why This Works Well:**  
- These colormaps are designed specifically for categorical data.
- They provide a variety of hues that are not simply a linear hue gradient.
- Helps prevent confusion by offering better contrast and variety.

**Function Snippet:**  
```python
def generate_distinct_colors(n):
    from matplotlib import pyplot as plt
    from matplotlib.colors import to_hex

    cmaps = [plt.get_cmap('tab20'), plt.get_cmap('tab20b'), plt.get_cmap('tab20c')]
    colors = []
    for cm in cmaps:
        for i in range(cm.N):
            colors.append(to_hex(cm(i)))
    return colors[:n]
