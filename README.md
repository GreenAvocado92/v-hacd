# The V-HACD library decomposes a 3D surface into a set of "near" convex parts.

# Installing

For Linux:

```bash
sudo apt install libcgal-dev # 5.0.2-3
mkdir build& cd build
cmake ..
make -j4
```

# Test

```bash
./main test.obj -o stl
./main test.ply -o stl
```
