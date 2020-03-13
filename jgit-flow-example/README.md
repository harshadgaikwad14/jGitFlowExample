# JGIT MAVEN FLOW

## Release Process Example (Develop and Hotfix[Master] Release)
Sample Example :
`https://gist.github.com/lemiorhan/97b4f827c08aed58a9d8`
`https://github.com/revof11/jgit-flow-maven`

## Current Application Version
    Master		<version>3.0.0</version>
    Develop	 	<version>3.0.1-SNAPSHOT</version>

## Getting started
* [Develop Release](#markdown-header-developrelease)
* [HotFix Release](#markdown-header-hotfixrelease)



## Prerequisite
Ensure local installation of following softwares/tools:

* JDK - 1.8
* Git (2.9.0 or higher) - only for cloning project from repository
* Apache Maven (3.3.9 or higher)

## Develop Release
~~~bash
# Git Pull On Develop Branch And Checkout New Feature Branch
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git checkout -b feature/03

# Code Commit To Feature Branch
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (feature/03)
$ git commit -am"feature 03 changes"
warning: LF will be replaced by CRLF in jgit-flow-example/src/main/java/com/test/Test.java.
The file will have its original line endings in your working directory.
[feature/03 1bb8e9d] feature 03 changes
 1 file changed, 1 insertion(+)

# Code Push To Feature Branch
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (feature/03)
$ git push
fatal: The current branch feature/03 has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin feature/03


harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (feature/03)
$ git push --set-upstream origin feature/03
Counting objects: 9, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (9/9), 615 bytes | 12.00 KiB/s, done.
Total 9 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
remote:
remote: Create a pull request for 'feature/03' on GitHub by visiting:
remote:      https://github.com/harshadgaikwad14/jGitFlowExample/pull/new/feature/03
remote:
To https://github.com/harshadgaikwad14/jGitFlowExample.git
 * [new branch]      feature/03 -> feature/03
Branch 'feature/03' set up to track remote branch 'feature/03' from 'origin'.

# Code Sync/Merge with Feature to develop
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (feature/03)
$ git checkout develop
Switched to branch 'develop'
Your branch is up to date with 'origin/develop'.

harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git merge feature/03
Updating 6ea9af2..1bb8e9d
Fast-forward
 jgit-flow-example/src/main/java/com/test/Test.java | 1 +
 1 file changed, 1 insertion(+)

# Merge Code Push To Develop
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git status
On branch develop
Your branch is ahead of 'origin/develop' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git push
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/harshadgaikwad14/jGitFlowExample.git
   6ea9af2..1bb8e9d  develop -> develop

# Checkout Feature Branch For Release Process
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git checkout feature/03
Switched to branch 'feature/03'
Your branch is up to date with 'origin/feature/03'.

harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (feature/03)
$ git branch -a
  develop
* feature/03
  master
  remotes/origin/HEAD -> origin/master
  remotes/origin/develop
  remotes/origin/feature/01
  remotes/origin/feature/02
  remotes/origin/feature/03
  remotes/origin/master

# Delete all the local branches except release fearure branch
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (feature/03)
$ git branch -D develop
Deleted branch develop (was 1bb8e9d).

harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (feature/03)
$ git branch -D master
Deleted branch master (was 7825a2e).

# Release Start On Feature Branch
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (feature/03)
$ mvn jgitflow:release-start
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building jgit-flow-example 3.0.1-SNAPSHOT
[INFO] ------------------------------------------------------------------------
[INFO]
[INFO] --- jgitflow-maven-plugin:1.0-m5.1:release-start (default-cli) @ jgit-flow-example ---
[INFO] detected cygwin:
[INFO]     - turning off filemode...
[INFO]     - fixing maven prompter...
[INFO] (develop) Checking for SNAPSHOT version in projects...
[INFO] (develop) Checking dependencies and plugins for snapshots ...
What is the release version for "jgit-flow-example"? (com.test:jgit-flow-example) [3.0.1]: << ** NOTE : If Required Change the version of Master/Release Branch Ex : 4.0.0 **>>

[INFO] (release/3.0.1) adding snapshot to pom versions...
[INFO] (release/3.0.1) updating poms for all projects...
[INFO] turn on debug logging with -X to see exact changes
[INFO] (release/3.0.1) updating pom for jgit-flow-example...
What is the development version for "jgit-flow-example"? (com.test:jgit-flow-example) [3.0.2-SNAPSHOT]: << ** NOTE : If Required Change the version of develop Branch Ex : 4.0.1-SNAPSHOT **>>

[INFO] (develop) updating poms with next development version...
[INFO] (develop) updating poms for all projects...
[INFO] turn on debug logging with -X to see exact changes
[INFO] (develop) updating pom for jgit-flow-example...
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 18.756 s
[INFO] Finished at: 2020-03-12T19:45:00+05:30
[INFO] Final Memory: 16M/190M
[INFO] ------------------------------------------------------------------------

# Finish Release Process
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (release/3.0.1)
$ mvn jgitflow:release-finish
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building jgit-flow-example 3.0.1-SNAPSHOT
[INFO] ------------------------------------------------------------------------
[INFO]
[INFO] --- jgitflow-maven-plugin:1.0-m5.1:release-finish (default-cli) @ jgit-flow-example ---
[INFO] detected cygwin:
[INFO]     - turning off filemode...
[INFO]     - fixing maven prompter...
[INFO] running jgitflow release finish...
[INFO] (release/3.0.1) Updating poms for RELEASE
[INFO] (release/3.0.1) removing snapshot from pom versions...
[INFO] (release/3.0.1) updating poms for all projects...
[INFO] turn on debug logging with -X to see exact changes
[INFO] (release/3.0.1) updating pom for jgit-flow-example...
[INFO] (release/3.0.1) Checking for RELEASE version in projects...
[INFO] (release/3.0.1) Checking dependencies and plugins for snapshots ...
[INFO] Executing: cmd.exe /X /C ""D:\Windows 7 (64-bit)\Apache Maven\apache-maven-3.3.9-bin\apache-maven-3.3.9\bin\mvn" -s C:\Users\HARSHA~1.GAI\AppData\Local\Temp\release-settings3404693175692587695.xml clean install --no-plugin-updates -DperformRelease=true -Partifactory"
    [WARNING] Command line option -npu is deprecated and will be removed in future Maven versions.
    [INFO] Scanning for projects...
    [WARNING]
    [WARNING] Some problems were encountered while building the effective model for com.test:jgit-flow-example:jar:3.0.1
    [WARNING] 'build.plugins.plugin.version' for org.apache.maven.plugins:maven-source-plugin is missing.
    [WARNING] 'build.plugins.plugin.version' for org.apache.maven.plugins:maven-deploy-plugin is missing.
    [WARNING]
    [WARNING] It is highly recommended to fix these problems because they threaten the stability of your build.
    [WARNING]
    [WARNING] For this reason, future Maven versions might no longer support building such malformed projects.
    [WARNING]
    [INFO]
    [INFO] ------------------------------------------------------------------------
    [INFO] Building jgit-flow-example 3.0.1
    [INFO] ------------------------------------------------------------------------
    [INFO]
    [INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ jgit-flow-example ---
    [INFO] Deleting D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target
    [INFO]
    [INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ jgit-flow-example ---
    [WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent!
    [INFO] Copying 0 resource
    [INFO]
    [INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ jgit-flow-example ---
    [INFO] Changes detected - recompiling the module!
    [WARNING] File encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent!
    [INFO] Compiling 1 source file to D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\classes
    [INFO]
    [INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ jgit-flow-example ---
    [WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent!
    [INFO] Copying 0 resource
    [INFO]
    [INFO] --- maven-compiler-plugin:3.1:testCompile (default-testCompile) @ jgit-flow-example ---
    [INFO] Nothing to compile - all classes are up to date
    [INFO]
    [INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ jgit-flow-example ---
    [INFO]
    [INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ jgit-flow-example ---
    [INFO] Building jar: D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.1.jar
    [INFO]
    [INFO] >>> maven-source-plugin:3.2.1:jar (attach-sources) > generate-sources @ jgit-flow-example >>>
    [INFO]
    [INFO] <<< maven-source-plugin:3.2.1:jar (attach-sources) < generate-sources @ jgit-flow-example <<<
    [INFO]
    [INFO] --- maven-source-plugin:3.2.1:jar (attach-sources) @ jgit-flow-example ---
    [INFO] Building jar: D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.1-sources.jar
    [INFO]
    [INFO] --- maven-javadoc-plugin:2.10.2:jar (attach-javadocs) @ jgit-flow-example ---
    [WARNING] Source files encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent!
    [INFO]
    Loading source files for package com.test...
    Constructing Javadoc information...
    Standard Doclet version 1.8.0_162
    Building tree for all the packages and classes...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\Test.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\package-frame.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\package-summary.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\package-tree.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\constant-values.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\class-use\Test.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\package-use.html...
    Building index for all the packages and classes...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\overview-tree.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\index-all.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\deprecated-list.html...
    Building index for all classes...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\allclasses-frame.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\allclasses-noframe.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\index.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\help-doc.html...
    [INFO] Building jar: D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.1-javadoc.jar
    [INFO]
    [INFO] --- maven-install-plugin:2.4:install (default-install) @ jgit-flow-example ---
    [INFO] Installing D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.1.jar to C:\Users\harshad.gaikwad\.m2\repository\com\test\jgit-flow-example\3.0.1\jgit-flow-example-3.0.1.jar
    [INFO] Installing D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\pom.xml to C:\Users\harshad.gaikwad\.m2\repository\com\test\jgit-flow-example\3.0.1\jgit-flow-example-3.0.1.pom
    [INFO] Installing D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.1-sources.jar to C:\Users\harshad.gaikwad\.m2\repository\com\test\jgit-flow-example\3.0.1\jgit-flow-example-3.0.1-sources.jar
    [INFO] Installing D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.1-javadoc.jar to C:\Users\harshad.gaikwad\.m2\repository\com\test\jgit-flow-example\3.0.1\jgit-flow-example-3.0.1-javadoc.jar
    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD SUCCESS
    [INFO] ------------------------------------------------------------------------
    [INFO] Total time: 13.470 s
    [INFO] Finished at: 2020-03-12T19:45:52+05:30
    [INFO] Final Memory: 23M/311M
    [INFO] ------------------------------------------------------------------------
[INFO] (develop) copying pom versions...
[INFO] (develop) updating poms for all projects...
[INFO] turn on debug logging with -X to see exact changes
[INFO] (develop) updating pom for jgit-flow-example...
[INFO] copying pom versions...
[INFO] (develop) updating poms for all projects...
[INFO] turn on debug logging with -X to see exact changes
[INFO] (develop) updating pom for jgit-flow-example...
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 29.976 s
[INFO] Finished at: 2020-03-12T19:45:54+05:30
[INFO] Final Memory: 13M/188M
[INFO] ------------------------------------------------------------------------

# Sync master and develop branch
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git push --all
Counting objects: 11, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (11/11), done.
Writing objects: 100% (11/11), 1.15 KiB | 33.00 KiB/s, done.
Total 11 (delta 7), reused 0 (delta 0)
remote: Resolving deltas: 100% (7/7), completed with 2 local objects.
To https://github.com/harshadgaikwad14/jGitFlowExample.git
   1bb8e9d..6fbc0c0  develop -> develop
   7825a2e..c03db55  master -> master

# Push created tags
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git push --tags
Counting objects: 1, done.
Writing objects: 100% (1/1), 183 bytes | 6.00 KiB/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/harshadgaikwad14/jGitFlowExample.git
 * [new tag]         release_3.0.1 -> release_3.0.1

harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
~~~
---

## HotFix Release
~~~bash
# Check Existing Tags
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git tag
release_1.0.0
release_1.0.1-fourth-hotfix
release_1.0.1-hotfix-1
release_1.0.2-hotfix-1
release_2.0.1-hotfix
release_2.0.2-hotfix
release_3.0.0
release_3.0.1
release_3.0.1-hotfix

# Hot Fix Release Always given from master branch.Switched to master branch
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.

harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (master)
$ git pull
Already up to date.


# Do your hotfix Code changes
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (master)
$ git status
git On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   src/main/java/com/test/Test.java

no changes added to commit (use "git add" and/or "git commit -a")

# Only Commit your code in master ..dont push your code in master branch
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (master)
$ git commit -am"hotfix-feature03"
warning: LF will be replaced by CRLF in jgit-flow-example/src/main/java/com/test/Test.java.
The file will have its original line endings in your working directory.
[master 323b1fa] hotfix-feature03
 1 file changed, 2 insertions(+), 1 deletion(-)

# Delete other local branch .. except master branch
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (master)
$ git branch -a
  develop
  feature/03
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/develop
  remotes/origin/feature/01
  remotes/origin/feature/02
  remotes/origin/feature/03
  remotes/origin/master

harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (master)
$ git branch -D develop
Deleted branch develop (was 6fbc0c0).
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (master)
$ git branch -D feature/03
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (master)
$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/develop
  remotes/origin/feature/01
  remotes/origin/feature/02
  remotes/origin/feature/03
  remotes/origin/master

# Start Your Hotfix release process
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (master)
$ mvn jgitflow:hotfix-start
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building jgit-flow-example 3.0.1
[INFO] ------------------------------------------------------------------------
[INFO]
[INFO] --- jgitflow-maven-plugin:1.0-m5.1:hotfix-start (default-cli) @ jgit-flow-example ---
[INFO] detected cygwin:
[INFO]     - turning off filemode...
[INFO]     - fixing maven prompter...
[INFO] (master) Checking for RELEASE version in projects...
[INFO] (master) Checking dependencies and plugins for snapshots ...
What is the hotfix version for "jgit-flow-example"? (com.test:jgit-flow-example) [3.0.2]: 3.0.2-hotfix
3.0.2-hotfix
[INFO] (hotfix/3.0.2-hotfix) adding snapshot to pom versions...
[INFO] (hotfix/3.0.2-hotfix) updating poms for all projects...
[INFO] turn on debug logging with -X to see exact changes
[INFO] (hotfix/3.0.2-hotfix) updating pom for jgit-flow-example...
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 30.849 s
[INFO] Finished at: 2020-03-13T10:45:17+05:30
[INFO] Final Memory: 16M/190M
[INFO] ------------------------------------------------------------------------

# Temporary branch will created as hotfix. Finish process will failed if any conflict is present in your files.so first resolved the conflict
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (hotfix/3.0.2-hotfix)
$ mvn jgitflow:hotfix-finish
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building jgit-flow-example 3.0.2-hotfix-SNAPSHOT
[INFO] ------------------------------------------------------------------------
[INFO]
[INFO] --- jgitflow-maven-plugin:1.0-m5.1:hotfix-finish (default-cli) @ jgit-flow-example ---
[INFO] detected cygwin:
[INFO]     - turning off filemode...
[INFO]     - fixing maven prompter...
[INFO] running jgitflow hotfix finish...
[INFO] (hotfix/3.0.2-hotfix) Updating poms for HOTFIX
[INFO] (hotfix/3.0.2-hotfix) removing snapshot from pom versions...
[INFO] (hotfix/3.0.2-hotfix) updating poms for all projects...
[INFO] turn on debug logging with -X to see exact changes
[INFO] (hotfix/3.0.2-hotfix) updating pom for jgit-flow-example...
[INFO] (hotfix/3.0.2-hotfix) Checking for RELEASE version in projects...
[INFO] (hotfix/3.0.2-hotfix) Checking dependencies and plugins for snapshots ...
[INFO] Executing: cmd.exe /X /C ""D:\Windows 7 (64-bit)\Apache Maven\apache-maven-3.3.9-bin\apache-maven-3.3.9\bin\mvn" -s C:\Users\HARSHA~1.GAI\AppData\Local\Temp\release-settings868082665001232348.xml clean install --no-plugin-updates -DperformRelease=true -Partifactory"
    [WARNING] Command line option -npu is deprecated and will be removed in future Maven versions.
    [INFO] Scanning for projects...
    [WARNING]
    [WARNING] Some problems were encountered while building the effective model for com.test:jgit-flow-example:jar:3.0.2-hotfix
    [WARNING] 'build.plugins.plugin.version' for org.apache.maven.plugins:maven-source-plugin is missing.
    [WARNING] 'build.plugins.plugin.version' for org.apache.maven.plugins:maven-deploy-plugin is missing.
    [WARNING]
    [WARNING] It is highly recommended to fix these problems because they threaten the stability of your build.
    [WARNING]
    [WARNING] For this reason, future Maven versions might no longer support building such malformed projects.
    [WARNING]
    [INFO]
    [INFO] ------------------------------------------------------------------------
    [INFO] Building jgit-flow-example 3.0.2-hotfix
    [INFO] ------------------------------------------------------------------------
    Downloading: https://igtb.jfrog.io/igtb/libs-release/org/apache/maven/plugins/maven-source-plugin/maven-metadata.xml
    Downloading: https://igtb.jfrog.io/igtb/libs-snapshot/org/apache/maven/plugins/maven-source-plugin/maven-metadata.xml
    Downloaded: https://igtb.jfrog.io/igtb/libs-snapshot/org/apache/maven/plugins/maven-source-plugin/maven-metadata.xml (932 B at 0.4 KB/sec)
    Downloaded: https://igtb.jfrog.io/igtb/libs-release/org/apache/maven/plugins/maven-source-plugin/maven-metadata.xml (932 B at 0.3 KB/sec)
    [INFO]
    [INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ jgit-flow-example ---
    [INFO] Deleting D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target
    [INFO]
    [INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ jgit-flow-example ---
    [WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent!
    [INFO] Copying 0 resource
    [INFO]
    [INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ jgit-flow-example ---
    [INFO] Changes detected - recompiling the module!
    [WARNING] File encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent!
    [INFO] Compiling 1 source file to D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\classes
    [INFO]
    [INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ jgit-flow-example ---
    [WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent!
    [INFO] Copying 0 resource
    [INFO]
    [INFO] --- maven-compiler-plugin:3.1:testCompile (default-testCompile) @ jgit-flow-example ---
    [INFO] Nothing to compile - all classes are up to date
    [INFO]
    [INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ jgit-flow-example ---
    [INFO]
    [INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ jgit-flow-example ---
    [INFO] Building jar: D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.2-hotfix.jar
    [INFO]
    [INFO] >>> maven-source-plugin:3.2.1:jar (attach-sources) > generate-sources @ jgit-flow-example >>>
    [INFO]
    [INFO] <<< maven-source-plugin:3.2.1:jar (attach-sources) < generate-sources @ jgit-flow-example <<<
    [INFO]
    [INFO] --- maven-source-plugin:3.2.1:jar (attach-sources) @ jgit-flow-example ---
    [INFO] Building jar: D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.2-hotfix-sources.jar
    [INFO]
    [INFO] --- maven-javadoc-plugin:2.10.2:jar (attach-javadocs) @ jgit-flow-example ---
    [WARNING] Source files encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent!
    [INFO]
    Loading source files for package com.test...
    Constructing Javadoc information...
    Standard Doclet version 1.8.0_162
    Building tree for all the packages and classes...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\Test.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\package-frame.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\package-summary.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\package-tree.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\constant-values.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\class-use\Test.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\package-use.html...
    Building index for all the packages and classes...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\overview-tree.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\index-all.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\deprecated-list.html...
    Building index for all classes...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\allclasses-frame.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\allclasses-noframe.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\index.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\help-doc.html...
    [INFO] Building jar: D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.2-hotfix-javadoc.jar
    [INFO]
    [INFO] --- maven-install-plugin:2.4:install (default-install) @ jgit-flow-example ---
    [INFO] Installing D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.2-hotfix.jar to C:\Users\harshad.gaikwad\.m2\repository\com\test\jgit-flow-example\3.0.2-hotfix\jgit-flow-example-3.0.2-hotfix.jar
    [INFO] Installing D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\pom.xml to C:\Users\harshad.gaikwad\.m2\repository\com\test\jgit-flow-example\3.0.2-hotfix\jgit-flow-example-3.0.2-hotfix.pom
    [INFO] Installing D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.2-hotfix-sources.jar to C:\Users\harshad.gaikwad\.m2\repository\com\test\jgit-flow-example\3.0.2-hotfix\jgit-flow-example-3.0.2-hotfix-sources.jar
    [INFO] Installing D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.2-hotfix-javadoc.jar to C:\Users\harshad.gaikwad\.m2\repository\com\test\jgit-flow-example\3.0.2-hotfix\jgit-flow-example-3.0.2-hotfix-javadoc.jar
    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD SUCCESS
    [INFO] ------------------------------------------------------------------------
    [INFO] Total time: 19.800 s
    [INFO] Finished at: 2020-03-13T10:46:08+05:30
    [INFO] Final Memory: 25M/277M
    [INFO] ------------------------------------------------------------------------
[INFO] (develop) copying pom versions...
[INFO] (develop) updating poms for all projects...
[INFO] turn on debug logging with -X to see exact changes
[INFO] (develop) updating pom for jgit-flow-example...
[INFO] copying pom versions...
[INFO] (develop) updating poms for all projects...
[INFO] turn on debug logging with -X to see exact changes
[INFO] (develop) updating pom for jgit-flow-example...
[WARNING] Error running JGitFlow Extension
com.atlassian.jgitflow.core.exception.JGitFlowExtensionException: Error updating develop poms to previously cached versions
        at com.atlassian.maven.plugins.jgitflow.extension.command.UpdateDevelopWithPreviousVersionsCommand.execute(UpdateDevelopWithPreviousVersionsCommand.java:70)
        at com.atlassian.jgitflow.core.command.AbstractGitFlowCommand.runExtensionCommands(AbstractGitFlowCommand.java:255)
        at com.atlassian.jgitflow.core.command.AbstractBranchMergingCommand.doMerge(AbstractBranchMergingCommand.java:94)
        at com.atlassian.jgitflow.core.command.AbstractBranchMergingCommand.doMerge(AbstractBranchMergingCommand.java:44)
        at com.atlassian.jgitflow.core.command.AbstractBranchMergingCommand.doMerge(AbstractBranchMergingCommand.java:39)
        at com.atlassian.jgitflow.core.command.HotfixFinishCommand.call(HotfixFinishCommand.java:128)
        at com.atlassian.maven.plugins.jgitflow.manager.DefaultFlowHotfixManager.finish(DefaultFlowHotfixManager.java:93)
        at com.atlassian.maven.plugins.jgitflow.mojo.HotfixFinishMojo.execute(HotfixFinishMojo.java:167)
        at org.apache.maven.plugin.DefaultBuildPluginManager.executeMojo(DefaultBuildPluginManager.java:134)
        at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:207)
        at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:153)
        at org.apache.maven.lifecycle.internal.MojoExecutor.execute(MojoExecutor.java:145)
        at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:116)
        at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject(LifecycleModuleBuilder.java:80)
        at org.apache.maven.lifecycle.internal.builder.singlethreaded.SingleThreadedBuilder.build(SingleThreadedBuilder.java:51)
        at org.apache.maven.lifecycle.internal.LifecycleStarter.execute(LifecycleStarter.java:128)
        at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:307)
        at org.apache.maven.DefaultMaven.doExecute(DefaultMaven.java:193)
        at org.apache.maven.DefaultMaven.execute(DefaultMaven.java:106)
        at org.apache.maven.cli.MavenCli.execute(MavenCli.java:863)
        at org.apache.maven.cli.MavenCli.doMain(MavenCli.java:288)
        at org.apache.maven.cli.MavenCli.main(MavenCli.java:199)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:498)
        at org.codehaus.plexus.classworlds.launcher.Launcher.launchEnhanced(Launcher.java:289)
        at org.codehaus.plexus.classworlds.launcher.Launcher.launch(Launcher.java:229)
        at org.codehaus.plexus.classworlds.launcher.Launcher.mainWithExitCode(Launcher.java:415)
        at org.codehaus.plexus.classworlds.launcher.Launcher.main(Launcher.java:356)
Caused by: com.atlassian.maven.plugins.jgitflow.exception.MavenJGitFlowException: error committing pom changes: Cannot commit on a repo with state: MERGING
        at com.atlassian.maven.plugins.jgitflow.helper.DefaultProjectHelper.commitAllPoms(DefaultProjectHelper.java:138)
        at com.atlassian.maven.plugins.jgitflow.extension.command.UpdateDevelopWithPreviousVersionsCommand.execute(UpdateDevelopWithPreviousVersionsCommand.java:64)
        ... 29 more
Caused by: org.eclipse.jgit.api.errors.WrongRepositoryStateException: Cannot commit on a repo with state: MERGING
        at org.eclipse.jgit.api.CommitCommand.call(CommitCommand.java:178)
        at com.atlassian.maven.plugins.jgitflow.helper.DefaultProjectHelper.commitAllPoms(DefaultProjectHelper.java:133)
        ... 30 more
[ERROR] Error merging into develop:
[ERROR] Merge of revisions 97c4def5520a00762da44013a4cb05f457d2c0e4, a35aa398e711fcf3f4bbb9f7f6af183da468d3fa with base 7825a2ef84a0339c8157fddc3f81cd52a38ad6f1 using strategy recursive resulted in: Conflicting.
[ERROR] see .git/jgitflow.log for more info
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 35.950 s
[INFO] Finished at: 2020-03-13T10:46:11+05:30
[INFO] Final Memory: 14M/205M
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal external.atlassian.jgitflow:jgitflow-maven-plugin:1.0-m5.1:hotfix-finish (default-cli) on project jgit-flow-example: Error finishing hotfix: Error while merging hotfix! -> [Help 1]
[ERROR]
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR]
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoExecutionException

# Conflict encounter..So resolved the conflict first.
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop|MERGING)
$ git status
On branch develop
Your branch is ahead of 'origin/develop' by 1 commit.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:

        modified:   pom.xml

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   src/main/java/com/test/Test.java


harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop|MERGING)
$ git diff
warning: LF will be replaced by CRLF in jgit-flow-example/src/main/java/com/test/Test.java.
The file will have its original line endings in your working directory.
diff --cc jgit-flow-example/src/main/java/com/test/Test.java
index a7e3c64,03fa12f..0000000
--- a/jgit-flow-example/src/main/java/com/test/Test.java
+++ b/jgit-flow-example/src/main/java/com/test/Test.java

# Conflict Resolved commit and push to develop branch
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop|MERGING)
$ git commit -am"conflict resolved"
warning: LF will be replaced by CRLF in jgit-flow-example/src/main/java/com/test/Test.java.
The file will have its original line endings in your working directory.
[develop 50c43ad] conflict resolved

harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git push
Counting objects: 24, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (19/19), done.
Writing objects: 100% (24/24), 2.22 KiB | 40.00 KiB/s, done.
Total 24 (delta 9), reused 0 (delta 0)
remote: Resolving deltas: 100% (9/9), completed with 4 local objects.
To https://github.com/harshadgaikwad14/jGitFlowExample.git
   6fbc0c0..50c43ad  develop -> develop

# Back to Temporary hotfix/3.0.2-hotfix branch
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git checkout hotfix/3.0.2-hotfix
Switched to branch 'hotfix/3.0.2-hotfix'

# Start again the hotfix release finish process
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (hotfix/3.0.2-hotfix)
$ mvn jgitflow:hotfix-finish
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building jgit-flow-example 3.0.2-hotfix
[INFO] ------------------------------------------------------------------------
[INFO]
[INFO] --- jgitflow-maven-plugin:1.0-m5.1:hotfix-finish (default-cli) @ jgit-flow-example ---
[INFO] detected cygwin:
[INFO]     - turning off filemode...
[INFO]     - fixing maven prompter...
[INFO] running jgitflow hotfix finish...
[INFO] (hotfix/3.0.2-hotfix) Updating poms for HOTFIX
[INFO] (hotfix/3.0.2-hotfix) removing snapshot from pom versions...
[INFO] (hotfix/3.0.2-hotfix) updating poms for all projects...
[INFO] turn on debug logging with -X to see exact changes
[INFO] (hotfix/3.0.2-hotfix) updating pom for jgit-flow-example...
[INFO] (hotfix/3.0.2-hotfix) Checking for RELEASE version in projects...
[INFO] (hotfix/3.0.2-hotfix) Checking dependencies and plugins for snapshots ...
[INFO] Executing: cmd.exe /X /C ""D:\Windows 7 (64-bit)\Apache Maven\apache-maven-3.3.9-bin\apache-maven-3.3.9\bin\mvn" -s C:\Users\HARSHA~1.GAI\AppData\Local\Temp\release-settings6881832918284199883.xml clean install --no-plugin-updates -DperformRelease=true -Partifactory"
    [WARNING] Command line option -npu is deprecated and will be removed in future Maven versions.
    [INFO] Scanning for projects...
    [WARNING]
    [WARNING] Some problems were encountered while building the effective model for com.test:jgit-flow-example:jar:3.0.2-hotfix
    [WARNING] 'build.plugins.plugin.version' for org.apache.maven.plugins:maven-source-plugin is missing.
    [WARNING] 'build.plugins.plugin.version' for org.apache.maven.plugins:maven-deploy-plugin is missing.
    [WARNING]
    [WARNING] It is highly recommended to fix these problems because they threaten the stability of your build.
    [WARNING]
    [WARNING] For this reason, future Maven versions might no longer support building such malformed projects.
    [WARNING]
    [INFO]
    [INFO] ------------------------------------------------------------------------
    [INFO] Building jgit-flow-example 3.0.2-hotfix
    [INFO] ------------------------------------------------------------------------
    [INFO]
    [INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ jgit-flow-example ---
    [INFO] Deleting D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target
    [INFO]
    [INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ jgit-flow-example ---
    [WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent!
    [INFO] Copying 0 resource
    [INFO]
    [INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ jgit-flow-example ---
    [INFO] Changes detected - recompiling the module!
    [WARNING] File encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent!
    [INFO] Compiling 1 source file to D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\classes
    [INFO]
    [INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ jgit-flow-example ---
    [WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent!
    [INFO] Copying 0 resource
    [INFO]
    [INFO] --- maven-compiler-plugin:3.1:testCompile (default-testCompile) @ jgit-flow-example ---
    [INFO] Nothing to compile - all classes are up to date
    [INFO]
    [INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ jgit-flow-example ---
    [INFO]
    [INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ jgit-flow-example ---
    [INFO] Building jar: D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.2-hotfix.jar
    [INFO]
    [INFO] >>> maven-source-plugin:3.2.1:jar (attach-sources) > generate-sources @ jgit-flow-example >>>
    [INFO]
    [INFO] <<< maven-source-plugin:3.2.1:jar (attach-sources) < generate-sources @ jgit-flow-example <<<
    [INFO]
    [INFO] --- maven-source-plugin:3.2.1:jar (attach-sources) @ jgit-flow-example ---
    [INFO] Building jar: D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.2-hotfix-sources.jar
    [INFO]
    [INFO] --- maven-javadoc-plugin:2.10.2:jar (attach-javadocs) @ jgit-flow-example ---
    [WARNING] Source files encoding has not been set, using platform encoding Cp1252, i.e. build is platform dependent!
    [INFO]
    Loading source files for package com.test...
    Constructing Javadoc information...
    Standard Doclet version 1.8.0_162
    Building tree for all the packages and classes...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\Test.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\package-frame.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\package-summary.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\package-tree.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\constant-values.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\class-use\Test.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\com\test\package-use.html...
    Building index for all the packages and classes...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\overview-tree.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\index-all.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\deprecated-list.html...
    Building index for all classes...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\allclasses-frame.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\allclasses-noframe.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\index.html...
    Generating D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\apidocs\help-doc.html...
    [INFO] Building jar: D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.2-hotfix-javadoc.jar
    [INFO]
    [INFO] --- maven-install-plugin:2.4:install (default-install) @ jgit-flow-example ---
    [INFO] Installing D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.2-hotfix.jar to C:\Users\harshad.gaikwad\.m2\repository\com\test\jgit-flow-example\3.0.2-hotfix\jgit-flow-example-3.0.2-hotfix.jar
    [INFO] Installing D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\pom.xml to C:\Users\harshad.gaikwad\.m2\repository\com\test\jgit-flow-example\3.0.2-hotfix\jgit-flow-example-3.0.2-hotfix.pom
    [INFO] Installing D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.2-hotfix-sources.jar to C:\Users\harshad.gaikwad\.m2\repository\com\test\jgit-flow-example\3.0.2-hotfix\jgit-flow-example-3.0.2-hotfix-sources.jar
    [INFO] Installing D:\Harshad\Code\Checkout_BitBucket\jGitFlowExample\jGitFlowExample\jgit-flow-example\target\jgit-flow-example-3.0.2-hotfix-javadoc.jar to C:\Users\harshad.gaikwad\.m2\repository\com\test\jgit-flow-example\3.0.2-hotfix\jgit-flow-example-3.0.2-hotfix-javadoc.jar
    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD SUCCESS
    [INFO] ------------------------------------------------------------------------
    [INFO] Total time: 12.080 s
    [INFO] Finished at: 2020-03-13T10:49:38+05:30
    [INFO] Final Memory: 23M/219M
    [INFO] ------------------------------------------------------------------------
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 26.986 s
[INFO] Finished at: 2020-03-13T10:49:39+05:30
[INFO] Final Memory: 16M/192M
[INFO] ------------------------------------------------------------------------

# Sync master and develop
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git push --all
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/harshadgaikwad14/jGitFlowExample.git
   c03db55..a35aa39  master -> master

# Push all the tags 
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git push --tags
Counting objects: 1, done.
Writing objects: 100% (1/1), 191 bytes | 10.00 KiB/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/harshadgaikwad14/jGitFlowExample.git
 * [new tag]         release_3.0.2-hotfix -> release_3.0.2-hotfix

# Check all the tags
harshad.gaikwad@N8975 MINGW64 /d/Harshad/Code/Checkout_BitBucket/jGitFlowExample/jGitFlowExample/jgit-flow-example (develop)
$ git tag
release_1.0.0
release_1.0.1-fourth-hotfix
release_1.0.1-hotfix-1
release_1.0.2-hotfix-1
release_2.0.1-hotfix
release_2.0.2-hotfix
release_3.0.0
release_3.0.1
release_3.0.1-hotfix
release_3.0.2-hotfix


~~~
---
## Authors

* **Harshad Gaikwad**