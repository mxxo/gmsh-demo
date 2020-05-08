# Gmsh workshop 

A quick tour of Gmsh. 

The quickest way to get Gmsh is using the SDK. 
The SDK has C++, Python, C and Julia bindings and also the standalone Gmsh binary. 

The binary lives inside `gmsh-4.5.6-Linux64-sdk/bin`

## Linux, MacOS quickstart 
```shell 
mkdir gmsh-scripts && cd gmsh-scripts 
wget http://gmsh.info/bin/Linux/gmsh-4.5.6-Linux64-sdk.tgz -O /tmp/gmsh-sdk.tar.gz && 
tar -xvf /tmp/gmsh-sdk.tar.gz
# this last step is optional if you want to use the python bindings: 
export PYTHONPATH=${PYTHONPATH}:${PWD}/gmsh-4.5.6-Linux64-sdk/lib
```
## Windows quickstart 
Download the Windows SDK from https://gmsh.info/bin/Windows/gmsh-4.5.6-Windows64.zip and extract it. 
Link to it library 

### Testing the C++ bindings 
```shell 
echo "#include \"gmsh.h\"\n\nint main() {\n    gmsh::initialize();\n    gmsh::finalize();\n}" > basic.cpp
g++ -o basic -std=c++11 basic.cpp -Igmsh-4.5.6-Linux64-sdk/include -Lgmsh-4.5.6-Linux64-sdk/lib -lgmsh
./basic
```

### Testing the Python bindings  
```shell 
echo "import gmsh" >> basic.py 
python3 basic.py 
```

## Topics 
- using the GUI 
- geometry (built-in kernel, CAD kernel)
- meshing
- physical groups (how to group things together)
- mesh files (v2, v4) 
- node orderings
- options 
- using the API (C++, Python) 

## Links
- Main site: http://gmsh.info/
- Mesh format reference: http://gmsh.info/dev/doc/texinfo/gmsh.html#MSH-file-format
- Tutorial readme and table of contents: https://gitlab.onelab.info/gmsh/gmsh/-/blob/master/tutorial/README.txt
- API demos: https://gitlab.onelab.info/gmsh/gmsh/-/tree/master/tutorial
- Reference manual: http://gmsh.info/dev/doc/texinfo/gmsh.html
- A recent tutorial: https://bthierry.pages.math.cnrs.fr/tutorial/gmsh/

### API notes: 
- You can find in-code examples of each API function here: http://gmsh.info/dev/doc/texinfo/gmsh.html#Gmsh-API
- Error handling can be tricky. Gmsh will often try to silently continue if there's an error. 
