Been wrapping my head around a client-server model but a simpler more digestable example is to use it as a serializing logic.

Generate the stub file
```
protoc --python_out=. service.proto
```


`--python_out` outputs _pb2.py files which generate the class on runtime. (It works but very cryptic to read it)
`--pyi_out` outputs _pb2.pyi which is alalogues to class interface. (most IDEs respect it and can use it to infer the class structure)
`--mypy_out` bascially adds more strict types (need to read more about it so will use it later)

**Version Mismatch Error**

If you get `VersionError: Detected incompatible Protobuf Gencode/Runtime versions`:

```
gencode 7.34.0-rc2 runtime 6.33.5. Runtime version cannot be older than the linked gencode version
```

The protoc compiler version is newer than the python protobuf package. Runtime must be >= generated code version.

Fix: 
```
pip install --upgrade protobuf
```
(This happened because devcontainer had protoc 7.34 but pip package was 6.33)

