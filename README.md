# Code Analysis

See comments in `index.html` for instructions.

## Run

Open `index.html` in Google Chrome.

## Style Guide

### Git Commit Messages

- Use the present tense ("Add feature" not "Added feature")
- Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
- Limit the first line to 72 characters or less
- Reference issues and pull requests liberally
- Consider starting the commit message with an applicable emoji:
    - **Improvements**
        - :art: `:art:` when improving the format/structure of the code
        - :fire: `:fire:` when removing code or files
        - :tada: `:tada:` when adding a feature
        - :goat: `:goat:` when improving performance
    - **Misc**
        - :memo: `:memo:` when writing docs
    - **Dependencies**
        - :arrow_up: `:arrow_up:` when upgrading dependencies
        - :arrow_down: `:arrow_down:` when downgrading dependencies

### React Styles

- Always favor stateless components

### Code Review/Wishlist

* This code seems like a piece that would possibly be reused.  This should be refactored into an easily reusable React Component with JSX instead of doing things simply via ReactDOM.
* getPersonList method currently gets data from an apparently old endpoint, which returns an empty list.  This should be updated to use [the new dataset.](https://willowtreeapps.com/api/v1.0/profiles/)  [Line 106](https://github.com/bedoherty/code-analysis-web/blob/master/index.html#L106)
* In the data transformations, it's possibly better to switch out of regex matching and into the .split function due to the [better performance](https://jsperf.com/regex-split-test) [Line 127](https://github.com/bedoherty/code-analysis-web/blob/master/index.html#L127) and [Line 131](https://github.com/bedoherty/code-analysis-web/blob/master/index.html#L131)
* Inconsistencies between implementation of sortByFirstName and sortByLastName.  These are both essentially the same function so they should really have the same style. [Line 202](https://github.com/bedoherty/code-analysis-web/blob/master/index.html#L202) and [Line 204](https://github.com/bedoherty/code-analysis-web/blob/master/index.html#L204)
* Bad use of slice in sortObjListByProp and shuffleList.  The code should be using .slice(0) instead of .slice(1).  (I.e. `let result = objList.slice(1);`)  This creates a list minus the first element instead of a copy of the list as is intended. [Line 139](https://github.com/bedoherty/code-analysis-web/blob/master/index.html#L139) and [Line 184](https://github.com/bedoherty/code-analysis-web/blob/master/index.html#L184)
* The method sortByLastName is incorrect, it should be sorting by last name, not the reverse of the whole name.  I.e. something like `const sortByLastName = (personList) => {sortObjListByProp('firstName');}`  [Line 204](https://github.com/bedoherty/code-analysis-web/blob/master/index.html#L204)
* In order to allow for that fix to sortByLastName, the objects need to be modified to be split into first/last names by use of the getFirstName/getLastName functions.  I.e. `personList.map((person) => {person.firstName = getFirstName(person.name); person.lastName = getLastName(person.name);});`

The "fixed" version of this code is currently living on the dev branch, and the master branch is to retain the original version/comments.