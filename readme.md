# ReGitLint

Integrates the free
[CleanupCode](https://www.jetbrains.com/help/resharper/CleanupCode.html)
command line tool from ReSharper Command Line Tools with git to provide
low friction c# linting for teams without requiring everyone to install
[ReSharper](https://www.jetbrains.com/resharper/).

ReGitLint makes it easy to add git hooks and / or build server checks to
ensure code is formatted consistenlty and put and end to style wars.
Your team will be holding hands and singing kum ba yah in no time!

Formatting options are specified in
[.editorconfig](https://editorconfig.org/) so everyone can use their
favorite editor. There are many formatting options supported... Here's
[a reference](https://www.jetbrains.com/help/resharper/EditorConfig_Generalized.html)

Example Usage:

* Format everything

    `ReCleanWrap.exe format -s .\Example.sln`

* Format modified c# files

    `ReCleanWrap.exe format -s .\Example.sln -f Modified -p "*.cs"`

* Format all staged files

    `ReCleanWrap.exe format -s .\Example.sln -f Staged -p "*"`

* Format all files modified by commit 3796556

	`ReCleanWrap.exe format -s .\Example.sln -f Commits -a 3796556 -p "*"`

* Format all files modified between commit 6708090 and 3796556

    `ReCleanWrap.exe format -s .\Example.sln -f Commits -a 6708090 -b 3796556 -p "*"`

* Format staged files, return 1 if files change. Handy for git hooks.

    `ReCleanWrap.exe format -s .\Example.sln -f Staged -p "*" -d`

* Format files between commits and return 1 if files change. Handy for
  enforcing code formatting on build server.

    `ReCleanWrap.exe format -s .\Example.sln -f Commits -a 6708090 -b 3796556 -p "*" -d`

* Enforce code formatting on jenkins

    `ReCleanWrap.exe format -s .\Example.sln -f -p "*" -d Commits -a $env.GIT_PREVIOUS_SUCCESSFUL_COMMIT -b $env.GIT_COMMIT`