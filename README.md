# Colab

## Upload

### Choose Files
```python
from google.colab import files
uploaded = files.upload()
```

### From GDrive
```python
from google.colab import drive
drive.mount('/content/drive')
```
