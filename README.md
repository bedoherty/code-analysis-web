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
* getPersonList method currently gets data from an apparently old endpoint, which returns an empty list.  This should be updated to use [the new dataset.](https://willowtreeapps.com/api/v1.0/profiles/)
* In the data transformations, it's possibly better to switch out of regex matching and into the .split function due to the [better performance](https://jsperf.com/regex-split-test)