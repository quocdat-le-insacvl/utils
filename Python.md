Python
======

# Open 
```python
with open(file_name, 'r', encoding="utf8") as f:
    # split by line
    lines = f.read().splitlines()
```
# Plotly

## Import 
```python
import matplotlib.pyplot as plt
from plotly.subplots import make_subplots
import plotly.graph_objects as go
import plotly.figure_factory as ff
```

```python
import plotly.offline as py
py.init_notebook_mode(connected=True)
from plotly.offline import init_notebook_mode, iplot
init_notebook_mode(connected=True)
import plotly.offline as offline
offline.init_notebook_mode()
import cufflinks as cf
cf.go_offline()
import plotly.io as pio
pio.renderers.default = "notebook"
```

## Display table
```python
def plotly_table(df_, title=""):
    # Let's set the number of rows and columns
    fig_1 = make_subplots(rows=1, cols=1, subplot_titles=(""))

    # Setting table parameters
    fig_1.add_trace(go.Table(
        # columnorder=[1, 2],
        # columnwidth=[100, 50],
        header=dict(values=df_.columns,
                    line_color='darkslategray',
                    fill_color='Salmon',
                    height=30),
        cells=dict(values=df_.to_numpy().T,
                   line_color='darkslategray',
                   fill_color='White')))

    # Setting the parameters of the chart when displaying
    fig_1.update_layout(showlegend=False,
                        title_text=title,
                        title_font_size=16,
                        title_font_family='Arial',
                        title_x=0.5,
                        font=dict(family='Arial',
                                  size=12,
                                  color='black'))

    # Displaying the graph
    fig_1.show()
```

## Pie chart
```python 
index, values = [], []
for type_ in ['string', 'category', 'int64', 'float']:
    index.append(type_)
    values.append(len(df.select_dtypes(include=type_).columns))
df_ = pd.DataFrame({'labels': index,
                   'values': values
                  })
df_.iplot(kind='pie',labels='labels',values='values', title='Data type')
```
