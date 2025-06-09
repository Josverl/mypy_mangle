# Repro of issue https://github.com/python/mypy/issues/16658

Intall latest mypy from source on different operating systems.
### Windows 11
```
uv venv
.venv\Scripts\activate
uv pip install -U git+https://github.com/python/mypy.git
```


## Run stubgen 

stubgen .\check_mangle_import.py
Processed 1 modules
Generated out\check_mangle_import.pyi


### Expected output 
```python
from _typeshed import Incomplete

def polar(*args, **kwargs) -> Incomplete: ...

```

### Incorrect output on Wndows
```py
from _typeshed import Incomplete as Incomplete

def polar(*args, **kwargs) -> Incomplete: ...

```


Note that the stub is correctly generated on Ubuntu.