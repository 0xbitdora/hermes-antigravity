## 2024-10-15 - [Pathlib vs OS Path]
**Learning:** `Path(path).is_file()` is significantly slower than `os.path.isfile(path)` because of the object instantiation overhead. For functions called frequently with string inputs during path scanning, checking `isinstance(path, Path)` and falling back to `os.path.isfile(path)` yields a ~4x speedup.
**Action:** Always prefer `os.path` functions for hot path file checks unless object-oriented path manipulation is required.
