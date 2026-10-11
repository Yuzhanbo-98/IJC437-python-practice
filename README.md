# IJC437 Python Practice

Python practice notebooks from **IJC437 Introduction to Data Science** (MSc Data Science, University of Sheffield, 2026/27).
The four parts go from first steps in Python to pandas, web APIs and publishing work on GitHub. Every exercise is completed and the notebooks run top to bottom (the only error outputs are the course's deliberate error examples).

| Part | Topic | View | Run |
|---|---|---|---|
| 1 | Python basics: values, strings, lists, dictionaries | [Notebook](IntroPython_part1.ipynb) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Yuzhanbo-98/IJC437-python-practice/blob/main/IntroPython_part1.ipynb) |
| 2 | Control flow, functions, lambda, map/filter, NumPy | [Notebook](IntroPython_part2.ipynb) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Yuzhanbo-98/IJC437-python-practice/blob/main/IntroPython_part2.ipynb) |
| 3 | pandas DataFrames, CSV files, data cleaning | [Notebook](IntroPython_part3.ipynb) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Yuzhanbo-98/IJC437-python-practice/blob/main/IntroPython_part3.ipynb) |
| 4 | Packages, web APIs, error messages, GitHub | [Notebook](IntroPython_part4.ipynb) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Yuzhanbo-98/IJC437-python-practice/blob/main/IntroPython_part4.ipynb) |

---

## Part 1 — Python basics

**Google Colab** — notebooks, code vs text cells, running cells (`Shift+Enter`), saving to Drive.

**First steps**
- `print()`, comments with `#`, variables (`x = 2 + 3`), a cell shows the value of its **last line**
- `help(round)` to read about a function

**Numbers** (数字运算)

| Operator | Meaning | Example |
|---|---|---|
| `/` | division (always a float) | `7 / 2 → 3.5` |
| `//` | whole-number division (整除) | `7 // 2 → 3` |
| `%` | remainder (余数) | `7 % 2 → 1` |
| `**` | power | `2 ** 10 → 1024` |

- `0.1 + 0.2 == 0.3` is `False` (binary decimals) → compare with `round(..., 2)`

**Strings** (字符串)
- `'single'`, `"double"`, `"""multi-line"""`
- `.upper()` `.lower()` `.title()` `.strip()` `.replace(a, b)` `.split()` `.count()` `.startswith()`, `len()`, `"Data" in title`
- f-strings: `f"{name} has {n * 2} covers"`, formatting `f"{value:.2f}"`, `f"{share:.1%}"`
- `\t` tab, `\n` new line

**Types and conversion** (类型转换)
- `int` `float` `str` `bool` `list` `dict`, check with `type()`
- `int("6")`, `float(3)`, `str(3)`; `"6" + 1` → `TypeError`, `int("hello")` → `ValueError`

**Comparisons and logic**: `== != > < >= <=`, `and or not`, `in`
- `=` assigns, `==` compares (赋值 vs 比较)

**Lists** (列表)
- Index from 0, negative index from the end: `x[0]`, `x[-1]`
- Slicing `x[start:stop:step]` (stop is excluded), `x[::-1]` reverses
- `.append()` `.insert()` `.pop()` `.remove()` `.sort()` vs `sorted()`, `sum() min() max() len()`
- `copy = original` is the **same list** with two names; use `original.copy()` for a real copy
- Lists inside lists: `grid[0][2]`

**Dictionaries** (字典)
- `{"key": value}`, `d["key"]` (KeyError if missing), `d.get("key", default)`
- add/change `d["new"] = v`, delete `del d["k"]`, `.keys()` `.values()` `.items()`

---

## Part 2 — Control flow, functions and NumPy

**Decisions**: `if / elif / else` — Python stops at the first true condition, so order matters; indentation defines the block (缩进决定代码块).

**Loops**
- `for item in collection:`, `range(start, stop, step)` (stop excluded)
- Accumulator pattern: `total = 0` then `total += value`
- List comprehension: `[len(n) for n in names if ...]`
- `for k, v in d.items():`, `enumerate()`, nested loops, `break` / `continue`
- `while condition:` — something inside must eventually make it `False`

**Functions** (函数)
- `def name(params):` … `return value`; define before you call
- `print` shows a value, `return` hands it back for reuse
- Default arguments `def f(name, greeting="Hello")`, keyword arguments
- Local vs global variables (局部变量 / 全局变量)

**Lambda, map, filter, reduce**
- `lambda x: x * x`; `sorted(words, key=lambda w: len(w))`
- `list(map(len, words))`, `list(filter(lambda x: x > 4, xs))`, `functools.reduce`
- A list comprehension is usually clearer than `map` / `filter`

**NumPy** (`import numpy as np`)
- `np.array([...])` — arithmetic applies to every element (`a * 2`)
- `.dtype` `.shape`; boolean masks `a[a > 2]`, combine with `&` `|`
- `.mean() .sum() .min() .max()`, `np.median`, `np.percentile`, `np.sort`, `np.append` (returns a new array)
- 2-D arrays: `t[row, col]`, `t[:, 0]`, `t.sum(axis=1)` per row, `axis=0` per column

---

## Part 3 — pandas and data cleaning

**Packages**: `import pandas as pd`, `!pip install pandas`

**DataFrames** (表格)
- Create from a dictionary of lists: `pd.DataFrame({...})`, `.dtypes`
- Columns: `df["Gold"]` → Series, `df[["Country", "Gold"]]` → DataFrame
- Rows by position: `df.iloc[[0, 2]]`, `df.iloc[rows, cols]`
- Filtering: `df[df["Gold"] >= 27]`, `&` / `|`, `.isin([...])`, `.loc[condition, columns]`, `.query("Gold >= 27")`
- New columns: `df["Total"] = df["Gold"] + ...`, `.sum(axis=1)`; drop with `df.drop(columns="Total")`
- New rows: `pd.concat([df, new_row], ignore_index=True)`
- `.sort_values("Total", ascending=False)`, multiple keys
- Getting to know a table: `.head() .tail() .shape .columns .info() .describe()`
- `.apply(lambda ...)` or `.apply(named_function)` on a column

**Files**
- Mount Drive: `from google.colab import drive; drive.mount("/content/drive")`
- `pd.read_csv(path)`, `df.to_csv(path, index=False)`, `files.download()`

**Cleaning messy data** (数据清洗)
- Look first: `.info()`, `.isna().sum()`
- Text: `.str.strip().str.upper()`
- Duplicates: `.duplicated().sum()`, `.drop_duplicates().reset_index(drop=True)`
- Numbers stored as text add up as text (`"46" + "27"`) → `.astype(int)`
- Missing values: `.fillna(0)`
- Column names: `df.columns.str.strip().str.lower()`

**Final exercise — Rio 2016 medal table**: loaded `Rio2016.csv` (87 countries, already clean), added a Total column, kept the 29 countries with at least ten medals, added a gold share column and saved the result to Drive. Finding: the USA dominates (121 medals), but smaller teams such as Jamaica, Hungary and Croatia turned a higher share of their medals into gold.

---

## Part 4 — Packages, APIs, errors and GitHub

**Modules, packages, libraries** (模块 / 包 / 库)
- module = one `.py` file, package = a folder of modules, library = a collection of packages
- `import math as m`, `from datetime import datetime`, `import os` (`os.getcwd()`)
- Install with `!pip install requests` in Colab

**Web APIs** (data comes back as JSON → Python dicts and lists)
```python
response = requests.get(url, params=params)   # GET = fetch data
response.status_code                           # 200 = success
data = response.json()
data["current_weather"]["temperature"]
```
| Code | Meaning |
|---|---|
| 2xx | success (200) |
| 4xx | client error — problem with the request (404 Not Found, 401 Unauthorised) |
| 5xx | server error — the API had a problem |

APIs used: Open-Meteo weather (Sheffield, Leeds, 3-day hourly forecast saved to CSV), Cat Facts (10 facts with a `while` loop), ISS location (then the weather below the ISS).

**Reading errors**: read a traceback **from the bottom up** — last line = error type and message, lines above = where it happened.

| Error | Cause |
|---|---|
| `KeyError` | dictionary key does not exist |
| `TypeError` | incompatible types, e.g. `"5" + 10` |
| `IndexError` | list position out of range |
| `AttributeError` | method or property does not exist |
| `NameError` | variable not defined |
| `ValueError` / `ZeroDivisionError` | bad value, e.g. `int("abc")`, dividing by 0 |

Catch expected errors with `try: ... except ValueError: ...`.

**GitHub portfolio**: README + clean annotated notebooks + data/outputs folders. Colab → *File → Save a copy in GitHub* → choose repo → commit message → tick *Include a link to Colab*.

---

## Common mistakes to remember (复习提醒)

- `//` is whole-number division; the remainder is `%`
- `==` compares, `=` assigns — `rating == 4` does not set `rating`
- `count += 1`, not `count += count + 1`
- Don't name variables `list`, `sum`, `len` etc. — it hides the built-in function
- A function parameter name must match the name used inside the function
- Only the **last line** of a cell is displayed — use `print()` or `display()` for the others
- `slice[a:b]` excludes `b`; check you have all 12 months / all the data before computing
- In pandas, column names are case-sensitive (`"Country"` not `"country"`)
