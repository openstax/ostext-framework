# ost-framework

The `ost-framework` repository provides the infrastructure necessary to style
OpenStax textbooks in paged and non-paged formats. A few of the features
provided by this framework -

   - Tools to generate `skeletons` for the various possible content nestings,
     for standard and custom content types.
   - Versioned, documented set of available `slots` and parameterization.
   - Paged Media features: Crop and Cross marks, Page/Margin sizes, Folio
     features, Pagebreaking and associated debug styling, etc.
   - Typographic features: Modular font scaling, Vertical rhythm and debug
     styling, etc.

### Developer Contributions

This section will describe the general practices a developer should follow
while contributing to `ost-framework` or `ost-templates`.

#### Code style

There are a few rules to follow with regards to coding style. These may run
aground of your own personal preference. Sorry, not sorry.

   - Indentation is 2 spaces. No tabs.
   - Avoid indirection unless you're prepared to provide Kropotkin levels of
     justification for it.

#### Git

Git usage should by and large follow the conventions and recommendations
used by Linux kernel developers at the direction of their BOFH. Although
not a 1:1 correlation with our own conventions, becoming familiar with
[Care And Operation Of Your Linus Torvalds](https://www.kernel.org/doc/Documentation/SubmittingPatches) is advised.

##### Commits

Generally speaking commits should be thought of in the sense used by git
commands such as cherry-pick, rebase, and revert: as a *patch*, based on
the changes that specific patch will introduce. Work should be performed as
a *patch series*, collectively shared using a [Pull Request](#pull-requests).

   - Commit messages are required. Describe changes using an imperative
     grammatical mood. Eg, `"Fix end of chapter solution numbering. #1234"`
   - When possible, include a reference to a Github Issue number in commit
     messages. See [Github](#github), and [Pull Requests](#pull-requests).
   - Solve only one problem per patch. If your commit message is verbose
     take this as an indication that you need to split your patch.
   - More specifically, avoid mixing types of patches. Eg, do not combine
     a bug fix and an optimization into a single patch, split these into
     a patch series. A project maintainer should be able to accept a Pull
     Request by only accepting individual patches in the patch series, and
     doing so should not break the individual logical changes performed in
     that series.
   - Ensure that after each patch the tree as a whole is working as intended.
     This will allow developers and maintainers to use `git-bisect` in order to
     track down problems.
   - Ensure that any `dist/` files are regenerated and commited with every
     patch. These types of rules seem strange, but preserve various git workflows.

#### Github

##### Milestones, Branches, Github Issues and Pull Requests

When addressing a problem or introducing features a developer should plan
this work as part of a Milestone, and structure branches/PRs/commits/issues
in a way that allows Github to combine these into a more useful composite.

The workflow we use requires the following:

   - Reference a Github Issue # in commit messages
   - Reference PR # in Github Issue comments
   - Work for a [release](#releases) is performed on a single, shared branch. You can
     work on your own branches, but merge all work into the common branch
     which the PR is attached to.

##### Pull Requests
   - Describe the problem being addressed.
   - Describe user-visible impact.

### Deployment

#### Testing

Once developers are confident a Github Issue is addressed it should
be reassigned to a QA team member for further testing/verification.

Github Issues are only closed by QA team members.

#### Code Review

Before releases are performed all code will undergo code review by all
developers. The goal of this review is not to optimise or refactor,
but to ensure consistency. Any required optimisation or refactoring should
be scheduled for a subsequent release.

#### Release

Releases are named and numbered; Any work performed should be discussed with
the textbook team and planned as a part of a release. Release numbers are tracked
in `version.txt`, which allows `DevOps` to easily verify release deployment.

After testing and code review is complete a developer will merge the branch
attached to the release Milestone, create a git Tag, and create a github Release.
Git Tag and github Release names are the same as the release number.