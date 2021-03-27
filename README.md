# PyInstaller-Error

### Environment

    Output of pyinstaller --version: 4.2.2
    Version of Python: 3.8.8
    Platform: Ubuntu 20.04


### Step-by-step guide to reproduce the error

1. Clone this repository
2. Change the pythex field in app.spec to point to your folder's path
3. Create a python venv
4. Run `pip install haystack`
5. Install the latest vestion of pyinstaller
6. Run `pyinstaller --onedir app.spec --clean --distpath distAPP`
7. Run ./distAPP/app/app

You should now get the error:
```
03/26/2021 22:23:58 - INFO - faiss -   Loading faiss with AVX2 support.
03/26/2021 22:23:58 - INFO - faiss -   Loading faiss.
Traceback (most recent call last):
  File "torch/_utils_internal.py", line 49, in get_source_lines_and_file
  File "inspect.py", line 979, in getsourcelines
  File "inspect.py", line 798, in findsource
OSError: could not get source code

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "app.py", line 1, in <module>
    from haystack.preprocessor.cleaning import clean_wiki_text
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller/loader/pyimod03_importers.py", line 531, in exec_module
  File "haystack/__init__.py", line 5, in <module>
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller/loader/pyimod03_importers.py", line 531, in exec_module
  File "haystack/finder.py", line 9, in <module>
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller/loader/pyimod03_importers.py", line 531, in exec_module
  File "haystack/retriever/base.py", line 9, in <module>
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller/loader/pyimod03_importers.py", line 531, in exec_module
  File "haystack/document_store/base.py", line 6, in <module>
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller/loader/pyimod03_importers.py", line 531, in exec_module
  File "haystack/preprocessor/utils.py", line 11, in <module>
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller/loader/pyimod03_importers.py", line 531, in exec_module
  File "farm/data_handler/utils.py", line 18, in <module>
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller/loader/pyimod03_importers.py", line 531, in exec_module
  File "farm/file_utils.py", line 26, in <module>
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller/loader/pyimod03_importers.py", line 531, in exec_module
  File "transformers/__init__.py", line 91, in <module>
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller/loader/pyimod03_importers.py", line 531, in exec_module
  File "transformers/modelcard.py", line 31, in <module>
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller/loader/pyimod03_importers.py", line 531, in exec_module
  File "transformers/models/auto/__init__.py", line 20, in <module>
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller/loader/pyimod03_importers.py", line 531, in exec_module
  File "transformers/models/auto/configuration_auto.py", line 28, in <module>
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller/loader/pyimod03_importers.py", line 531, in exec_module
  File "transformers/models/deberta/__init__.py", line 25, in <module>
  File "<frozen importlib._bootstrap>", line 991, in _find_and_load
  File "<frozen importlib._bootstrap>", line 975, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 671, in _load_unlocked
  File "PyInstaller/loader/pyimod03_importers.py", line 531, in exec_module
  File "transformers/models/deberta/modeling_deberta.py", line 462, in <module>
  File "torch/jit/_script.py", line 936, in script
  File "torch/jit/frontend.py", line 197, in get_jit_def
  File "torch/_utils_internal.py", line 56, in get_source_lines_and_file
OSError: Can't get source for <function c2p_dynamic_expand at 0x7ff34dfe7280>. TorchScript requires source access in order to carry out compilation, make sure original .py files are available.
[138475] Failed to execute script app

```

Refer to the issue at https://github.com/pyinstaller/pyinstaller/issues/5673 for further guidance on what happened next.
