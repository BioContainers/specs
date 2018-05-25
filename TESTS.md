Post-build testing
==================

Once an image has been correctly been built, additional test can be added to make sure the containers run properly.

## 1. Where to write tests

Test command should be written in a file called **test-cmds.txt**. This file must be located in the same directory as the **Dockerfile**.

## 2. How to write tests

Each line of the test file contains a single command whose correct execution will be tested. This means a _docker run_ command will be executed and its exit status tested for each (non empty) line in the test file.

The _docker run_ command looks like this:

> docker run -v [TESTDIRMOUNT](#23-extra-test-data) \[--entrypoint=[ENTRYPOINT](#21-entrypoint)\] image_name [ARGS](#22-other-arguments)

### 2.1. Entrypoint

Unless it starts with a dash "-" sign, the first term on each line will be considered as the test's _entrypoint_ (more details [here](https://docs.docker.com/engine/reference/run/#entrypoint-default-command-to-execute-at-runtime).

### 2.2. Other arguments

If there was an entrypoint, other terms will be used as arguments. Otherwise the entire line will be considered as arguments.

### 2.3. Extra test data

Some tests might require extra data (for example you may want to see if your _BLAST_ image can correctly build a database, requiring a test fasta file).
Those test data can be stored in the same directory as the Dockerfile. This same directory will be automatically mounted in the test containers at runtime in **/biocontainers**.

For example if your Dockerfile directory looks like this:

**.**
 * Dockerfile
 * test-cmds.txt
 * mytestdata
  * mySeq.fa

Then you can access the fasta file using this path: _/biocontainers/mytestdata/mySeq.fa_

## 3. Outcomes

### 3.1. No test file found

Whether there is no test file at all or it is not found for some reason (wrong name, not in the root directory...), this will result in a comment automatically posted in the associated Pull Request stating that no tests could be made.
Please note that this will **NOT** modify the PR status.

### 3.2. Tests run

#### 3.2.1. All tests succeeded

If each test was run with no error signal returned, then the post build testing status will be set to _success_ with a message stating that all tests ran correctly.

#### 3.2.2. A test ends in an error

As soon as a test exits with an error code then the testing status will be set to _failure_ and a message will display the guilty line's content.
