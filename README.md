# CodingGuidelines
Coding guidelines for the ALICE O2 project.

### Documents

* Coding guidelines
* Naming and formatting conventions
* Comments guidelines

### ClangFormat

ClangFormat can be used to format your source code. The configuration file. We provide to files, one for clang 4.4 and one for the versions above. 

* [_clang-format (< 4.5)](_clang-format-44)
* [_clang-format (>= 4.5)](_clang-format-45)

To use it (example for SLC6) : 
```
sudo yum install clang
cd <source code location>
cp _clang-format-44 ../.clang-format
clang-format -style=file -i SOURCEFILE # -i if you want to replace content
```

### Configuration files for editors
#### Eclipse

1. [Download](Eclipse_O2_formatting.xml),
2. Go to Project->Properties->C/C++ General->Formatter,
2. Select the option "Enable project specific settings",
3. Click on the "Import..." button.

#### CLion
1. [Download](settings-codestyle-clion.jar),
2. Go to File -> Import Settings. 
