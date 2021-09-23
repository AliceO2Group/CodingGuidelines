[![JIRA](https://img.shields.io/badge/JIRA-Report%20issue-blue.svg)](https://alice.its.cern.ch/jira/secure/CreateIssue.jspa?pid=11201&issuetype=1)

# ALICE O2 Coding Guidelines
Coding guidelines for the ALICE O2 project.

### Documents

* [Coding guidelines](https://rawgit.com/AliceO2Group/CodingGuidelines/master/coding_guidelines.html)
* [Naming and formatting conventions](https://rawgit.com/AliceO2Group/CodingGuidelines/master/naming_formatting.html)
* [Comments guidelines](https://rawgit.com/AliceO2Group/CodingGuidelines/master/comments_guidelines.html)

### Formatting tool
The ALICE O2 projects use `clang-format` to push for a common code formatting. The rules are defined in
the `clang-format` configuration file in this repository (which is propagated to other AliceO2Group repositories). With an adiabatic
approach, all changes have to follow the formatting rules. A script, described below, can be
used to integrate the formatting into `git` and suggest formatting only for
changed lines.

#### Install `clang-format` and git integration

Note : The installation of clang using aliBuild is not necessary on Mac.

1. Build clang (to be done once)
```bash
aliBuild build --defaults o2 Clang
```
2. Load clang and clang-format
```bash
alienv enter Clang/latest
```
3. Install git-clang-format
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
git clang-format origin/dev
```

#### Check files' formatting

The commands below rely on the [.clang-format](.clang-format) file located in one of the parent
directories of the source files.

Please note that for technical reasons, there are slight differences between `clang-format` and `git-clang-format` (see above). All pull requests are checked with `git-clang-format` as described in the previous bullet. Thus make sure that before pushing code, correct the formatting with `git-clang-format`. The instructions for `clang-format` are left here only for reference.

Show correctly formatted version of a file :
```
clang-format -style=file SOURCEFILE
```

Directly apply the style to a file :
```
clang-format -style=file -i SOURCEFILE
```

Apply the style to all the source and header files in a directory (recursive) :

```
find . -iname "*.h" -o -iname "*.cpp" | xargs clang-format -style=file -i
```

Display what needs to be fixed in a file :
```
clang-format -style=file <SOURCEFILE> | diff <SOURCEFILE> -
```

#### Using an IDE
A number of config files are available [here](https://github.com/AliceO2Group/CodingGuidelines) for various IDEs.

### O2 code checker
All the AliceO2 pull requests are subject to be tested with [O2 CodeChecker](https://github.com/AliceO2Group/O2CodeChecker#readme) during  `build/O2/fullCI` check. It is a bit stricter tool than `clang-format`. Contributors are encouraged to run the codecheck locally before creating a pull request in order to save checking time and CPU resources of the testing facilities. Try to run it in the root directory of your installation:
```
aliBuild build o2checkcode --defaults o2
```
In case of success you'll be informed of it:
```
==> Build of o2checkcode successfully completed on `your-pc-name'.
```
Otherwise an ERROR messages will appear:
```
==> Building o2checkcode@1.0
==> o2checkcode is being built (use --debug for full output): failed
ERROR: Error while executing /your/path/sw/SPECS/ubuntu2004_x86-64/o2checkcode/1.0-local1/build.sh on `your-pc-name'.
ERROR: Log can be found in /your/path/sw/BUILD/o2checkcode-latest/log
```
You'll find details of the problem at the __end__ of logfile: `/your/path/sw/BUILD/o2checkcode-latest/log`. For example:
```
========== List of errors found ==========
/sw/SOURCES/O2/7084-slc8_x86-64/0/Detectors/CPV/calib/include/CPVCalibration/PedestalCalibrator.h:78:3: error: use '= default' to define a trivial destructor [modernize-use-equals-default]
```
There could be other errors before `========== List of errors found ==========` but they are not relevant. Important ones go after the mentioned line.

The use of o2checkcode is tested at CC8/CS8 and Ubuntu 20.04.3 LTS. People reported failure of successful running o2checkcode on other systems. Alternative ways to run code checker are following:
1. Try above mentioned way in a Docker container used for CI tests, namely `alisw/slc8-gpu-builder`;
2. Run O2CodeChecker manually in build directory of O2 project. The instructions can be found [here](https://github.com/AliceO2Group/O2CodeChecker#usage).

### Configuration files for editors

#### CLion
1. [Download](https://github.com/AliceO2Group/CodingGuidelines/raw/master/settings-o2-codestyle-clion.jar),
2. Go to File -> Import Settings.

## FAQ
* __Q__ I strongly disagree with rule X !
* __A__ Feel free to contact the WP3 (alice-o2-wp3@cern.ch) to share your concern(s). Rules have already been amended, abandoned or added based on the users feedback. However, please comply with the rules until a change is agreed by CWG11.

