# PyWikiHow

An unofficial WikiWow python API. Uses BeautifulSoup to scrape WikiHow and return the data you want.

- [Installation](#install)
- [Usage](#usage)
  * [Random How To](#random-how-to)
  * [Searching](#searching)
  * [Parsing](#parsing)


## Installation
```bash
pip install pywikihow
```

## Usage

### Random How To

Learn random stuff! Retuns a random WikiHow article. Sometimes they're weird.

```python
from pywikihow import RandomHowTo

how_to = RandomHowTo()
how_to.print()

```

### Searching

```python
from pywikihow import WikiHow, search_wikihow


max_results = 1  # default for optional argument is 10
how_tos = search_wikihow("how to learn programming", max_results)
assert len(how_tos) == 1
how_tos[0].print()


# for efficiency and to get unlimited entries, the best is to use the generator
for how_to in WikiHow.search("how to learn python"):
    how_to.print()

```

### Parsing

Manipulate HowTo objects

```python
from pywikihow import HowTo

how_to = HowTo("https://www.wikihow.com/Train-a-Dog")

data = how_to.as_dict()

print(how_to.url)
print(how_to.title)
print(how_to.intro)
print(how_to.n_steps)
print(how_to.summary)

first_step = how_to.steps[0]
first_step.print()
data = first_step.as_dict()

how_to.print(extended=True)

```
Some articles have their topics subdivided into internal parts. The parent part of each step is kept on the field `part` of the step.

```python
print(first_step.part)
```

### ToDo


- Add parser for tips
- Add parser for warnings
