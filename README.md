# ALICE O2 Coding Guidelines
Coding guidelines for the ALICE O2 project.

### Documents

* [Coding guidelines](http://htmlpreview.github.com/?https://github.com/AliceO2Group/CodingGuidelines/blob/master/coding_guidelines.html)
* [Naming and formatting conventions](http://htmlpreview.github.com/?https://github.com/AliceO2Group/CodingGuidelines/blob/master/naming_formatting.html)
* [Comments guidelines](http://htmlpreview.github.com/?https://github.com/AliceO2Group/CodingGuidelines/blob/master/comments_guidelines.html)

### ClangFormat

ClangFormat can be used to format your source code. The configuration file. We provide to files, one for clang 4.4 and one for the versions above. 

* [_clang-format (< 4.5)](https://github.com/AliceO2Group/CodingGuidelines/raw/master/_clang-format-3)
* [_clang-format (>= 4.5)](https://github.com/AliceO2Group/CodingGuidelines/raw/master/_clang-format-4)

To use it (example for SLC6) : 
```
sudo yum install clang
cd <source code location>
cp _clang-format-4 ../.clang-format
clang-format -style=file -i SOURCEFILE # -i if you want to replace content
```

### Configuration files for editors
#### Eclipse

1. [Download](https://github.com/AliceO2Group/CodingGuidelines/raw/master/Eclipse_O2_formatting.xml),
2. Go to Project->Properties->C/C++ General->Formatter,
2. Select the option "Enable project specific settings",
3. Click on the "Import..." button.

#### CLion
1. [Download](https://github.com/AliceO2Group/CodingGuidelines/raw/master/settings-codestyle-clion.jar),
2. Go to File -> Import Settings. 

## FAQ
* __Q__ I strongly disagree with rule X !
* __A__ Feel free to contact the CWG11 (alice-o2-cwg11@cern.ch) to share your concern(s). Rules have already been amended, abandoned or added based on the users feedback. However, please comply with the rules until a change is agreed by CWG11.
 
