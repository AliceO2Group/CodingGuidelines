[![JIRA](https://img.shields.io/badge/JIRA-Report%20issue-blue.svg)](https://alice.its.cern.ch/jira/secure/CreateIssue.jspa?pid=11201&issuetype=1)

# ALICE O2 Coding Guidelines
Coding guidelines for the ALICE O2 project.

### Documents

* [Coding guidelines](https://rawgit.com/AliceO2Group/CodingGuidelines/master/coding_guidelines.html)
* [Naming and formatting conventions](https://rawgit.com/AliceO2Group/CodingGuidelines/master/naming_formatting.html)
* [Comments guidelines](https://rawgit.com/AliceO2Group/CodingGuidelines/master/comments_guidelines.html)

### C++ formatting tool
The ALICE O2 projects use `clang-format` to push for a common code formatting. The rules are defined in
the `.clang-format` configuration file in this repository (which is propagated to other AliceO2Group repositories). With an adiabatic
approach, all changes have to follow the formatting rules. A script, described below, can be
used to integrate the formatting into `git` and suggest formatting only for
changed lines.

#### Install `clang-format` and git integration

Note : The installation of Clang using aliBuild is not necessary on Mac.

1. Build Clang (to be done once)
```bash
aliBuild build --defaults o2 Clang
```
2. Load Clang and `clang-format`
```bash
alienv enter Clang/latest
```
3. Install `git-clang-format`
```bash
cd $HOME
mkdir -p bin
cd bin
wget https://raw.githubusercontent.com/llvm/llvm-project/main/clang/tools/clang-format/git-clang-format
chmod u+x git-clang-format
```

#### Check commits' formatting
`git clang-format` invokes `clang-format` on the changes in current files
or a specific commit. E.g. for the last commit
```
git clang-format HEAD~1
```

Or for all commits done with respect to the remote branch state
```
git clang-format upstream/dev
```

#### Check files' formatting
Please note that for technical reasons, there are slight differences between `clang-format` and `git-clang-format` (see above). All pull requests are checked with `git-clang-format` as described in the previous bullet. Thus make sure that before pushing code, correct the formatting with `git-clang-format`. The instructions for `clang-format` are left here only for reference.
Show correctly formatted version of a file:
```
clang-format -style=file <SOURCEFILE>
```

Directly apply the style to a file:
```
clang-format -style=file -i <SOURCEFILE>
```

Apply the style to all the source and header files in a directory (recursive):

```
find . -iname "*.h" -o -iname "*.cpp" | xargs clang-format -style=file -i
```

Display what needs to be fixed in a file:
```
clang-format -style=file <SOURCEFILE> | diff <SOURCEFILE> -
```

#### Using an IDE
A number of config files are available [here](https://github.com/AliceO2Group/CodingGuidelines) for various IDEs.

### CMake formatting and linting tools

CMake files should be formatted with `cmake-format` and linted with `cmake-lint`.
The rules are defined in a `.cmake-format.{py,yml,json}` file in the root directory of a repository.

#### Install `cmakelang`

```bash
pip3 install --user cmakelang
```

#### Format a file

```bash
cmake-format -i <SOURCEFILE>
```

#### Lint a file

```bash
cmake-lint <SOURCEFILE>
```

### Configuration files for editors

#### CLion
1. [Download](https://github.com/AliceO2Group/CodingGuidelines/raw/master/settings-o2-codestyle-clion.jar),
2. Go to File -> Import Settings.

## FAQ
* __Q__ I strongly disagree with rule X !
* __A__ Feel free to contact the WP3 (alice-o2-wp3@cern.ch) to share your concern(s). Rules have already been amended, abandoned or added based on the users feedback. However, please comply with the rules until a change is agreed by CWG11.

