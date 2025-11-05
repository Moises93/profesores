```markdown
# Contributing to profesores

## Welcome!

Thank you for your interest in contributing to profesores! We appreciate your help in making this project better. Whether you're fixing a bug, improving the documentation, or suggesting a new feature, your contributions are valuable. Here are some easy ways to get involved:

*   Report bugs
*   Suggest new features
*   Improve the documentation

## Code of Conduct

Our project values inclusivity and respect. We are committed to providing a welcoming and harassment-free environment for everyone.

*   Treat all contributors with respect and kindness.
*   Be mindful of your language and avoid offensive or discriminatory remarks.
*   We have zero tolerance for harassment of any kind, including but not limited to:
    *   Offensive verbal comments related to gender, gender identity and expression, sexual orientation, disability, physical appearance, body size, race, age, religion, or technology choices.
    *   Deliberate intimidation, stalking, or following.
    *   Harassing photography or recording.
    *   Sustained disruption of talks or other events.
    *   Inappropriate physical contact.
    *   Unwelcome sexual attention.

To report a violation of the Code of Conduct, please contact [maintainer's email address will be here]. All reports will be kept confidential and investigated thoroughly.

## Ways to Contribute

There are many ways to contribute to profesores:

*   **Report Bugs:** Help us identify and fix issues by reporting bugs.
*   **Suggest Features:** Propose new features and improvements to enhance profesores.
*   **Improve Documentation:** Make the project more accessible by improving the documentation.
*   **Write Tests:** Ensure the stability and reliability of profesores by writing tests.
*   **Answer Questions in Issues:** Help other users by answering questions in the issue tracker.
*   **Maintain Translations:** Contribute to the internationalization of profesores by maintaining translations.

## Reporting Bugs

When reporting a bug, please provide as much detail as possible to help us understand and reproduce the issue. Include the following information:

*   **Description:** A clear and concise description of the bug.
*   **Steps to Reproduce:** The exact steps to reproduce the bug.
*   **Expected Behavior:** What you expected to happen.
*   **Actual Behavior:** What actually happened.
*   **Environment:** Your operating system, browser, and versions of relevant libraries.
*   **Error Messages:** Any error messages you received.

Use the following format for your bug report:

```
## Bug Report

**Description:** [A clear and concise description of the bug]

**Steps to Reproduce:**
1. [Step 1]
2. [Step 2]
3. [Step 3]

**Expected Behavior:** [What you expected to happen]

**Actual Behavior:** [What actually happened]

**Environment:**
- OS: [Operating System]
- Browser: [Browser]
- Version: [Version]

**Error Messages:** [Any error messages you received]
```

Report bugs in the [issues section](https://github.com/Moises93/profesores/issues). Use the "Bug Report" template when creating a new issue.

## Suggesting Features

When suggesting a feature, please provide a clear and concise description of the feature and its benefits. Include the following information:

*   **Description:** A clear and concise description of the feature.
*   **Use Case:** How the feature will be used and who will benefit from it.
*   **Examples:** Examples of how the feature could be implemented.

Use the following format for your feature request:

```
## Feature Request

**Description:** [A clear and concise description of the feature]

**Use Case:** [How the feature will be used and who will benefit from it]

**Examples:** [Examples of how the feature could be implemented]
```

Submit feature requests in the [issues section](https://github.com/Moises93/profesores/issues). Use the "Feature Request" template when creating a new issue.

## Development Setup

To set up your development environment, follow these steps:

1.  **Fork the repository:** Click the "Fork" button on the top right of the [repository page](https://github.com/Moises93/profesores.git).
2.  **Clone your fork:**
    ```bash
    git clone https://github.com/[your_username]/profesores.git
    cd profesores
    ```
3.  **Install development dependencies:**
    ```bash
    # Example using pip (if it's a Python project)
    pip install -r requirements.txt

    # Example using npm (if it's a Javascript/Typescript project)
    npm install
    ```

    *Note: Replace `requirements.txt` or `npm install` with the appropriate command for the project's technology stack.*
4.  **Run tests locally:**
    ```bash
    # Example using pytest (Python)
    pytest

    # Example using Jest (Javascript/Typescript)
    npm test
    ```
5.  **Recommended Tools:**
    *   [Your preferred IDE - e.g., VS Code, PyCharm, IntelliJ]
    *   [Git](https://git-scm.com/)
    *   [A terminal - e.g., iTerm2, Windows Terminal]

6.  **IDE Setup:**
    *   Configure your IDE to use the project's code style (see Code Style Guide below).
    *   Install relevant plugins for linting and formatting.

## Workflow: Fork → Branch → PR

Here's the standard workflow for contributing to profesores:

1.  **Fork the repository:** As described above.
2.  **Clone your fork:** As described above.
3.  **Create a descriptive branch name:**
    *   Use the following naming convention: `feature/your-feature-name` or `fix/your-fix-name`.
    ```bash
    git checkout -b feature/add-new-feature
    ```
4.  **Make changes:** Implement your feature or fix the bug.
5.  **Make clear commits:** Write clear and concise commit messages (see Commits and Messages below).
    ```bash
    git add .
    git commit -m "feat: Add new feature"
    ```
6.  **Push to your branch:**
    ```bash
    git push origin feature/add-new-feature
    ```
7.  **Create a Pull Request:** Go to the original [repository page](https://github.com/Moises93/profesores.git) and click the "Compare & pull request" button.
8.  **Respond to reviews:** Address any feedback from reviewers and make necessary changes.
9.  **Merge:** Once your pull request is approved, it will be merged into the `master` branch.

## Code Style Guide

Please follow these code style guidelines to ensure consistency and maintainability:

**Python:**

*   **PEP 8:** Adhere to the PEP 8 style guide.
*   **Type Hints:** Use type hints to improve code readability and maintainability.
*   **Docstrings:** Write clear and concise docstrings for all functions and classes.

```python
# Good
def add(x: int, y: int) -> int:
    """Adds two numbers together.

    Args:
        x: The first number.
        y: The second number.

    Returns:
        The sum of x and y.
    """
    return x + y

# Bad
def add(x, y):
    return x + y
```

**JavaScript/TypeScript:**

*   **ESLint Config:** Use the project's ESLint configuration.
*   **Prettier Format:** Format your code using Prettier.
*   **Naming Conventions:** Follow consistent naming conventions for variables, functions, and classes.

```javascript
// Good
const myVariable = "hello";

function myFunction() {
  // ...
}

// Bad
var MyVariable = "hello";

function my_function() {
  // ...
}
```

**General Conventions:**

*   Use meaningful variable and function names.
*   Write clear and concise code.
*   Avoid unnecessary complexity.
*   Add comments to explain complex logic.

## Testing

We use [Testing Framework - e.g., pytest, Jest] for testing.

*   **How to run tests:**
    ```bash
    # Example using pytest (Python)
    pytest

    # Example using Jest (Javascript/Typescript)
    npm test
    ```
*   **Expected coverage:** Aim for [Desired Coverage Percentage - e.g., 80%] test coverage.
*   **How to write tests:** Write tests that cover all critical functionality and edge cases.

```python
# Example test (Python)
def test_add():
    assert add(2, 3) == 5
```

```javascript
// Example test (Javascript/Typescript)
test('adds 1 + 2 to equal 3', () => {
  expect(1 + 2).toBe(3);
});
```

## Commits and Messages

We follow the Conventional Commits specification for commit messages. This helps us automate the release process and generate changelogs.

*   **Types:**
    *   `feat`: A new feature.
    *   `fix`: A bug fix.
    *   `docs`: Documentation changes.
    *   `style`: Code style changes (formatting, linting).
    *   `refactor`: Code refactoring (no feature change or bug fix).
    *   `test`: Adding or modifying tests.
    *   `chore`: Build process or auxiliary tool changes.

*   **Good Message Examples:**
    *   `feat: Add user authentication`
    *   `fix: Resolve issue with incorrect calculation`
    *   `docs: Update README with installation instructions`

*   **Atomic Commits:** Make small, focused commits that address a single issue or feature.
*   **Why it matters:** Well-structured commit messages make it easier to understand the history of the project and automate releases.

## Pull Request Process

To ensure a smooth pull request process, please follow these guidelines:

*   **Ensure updated with main:** Before submitting a pull request, make sure your branch is up-to-date with the `master` branch.
    ```bash
    git pull origin master
    ```
*   **Include a clear description:** Provide a clear and concise description of the changes you've made in the pull request.
*   **Reference related issues:** If your pull request addresses a specific issue, reference it in the description (e.g., "Fixes #123").
*   **Respond to feedback:** Be responsive to feedback from reviewers and make necessary changes.
*   **Be patient with reviews:** Code review takes time, so be patient and wait for reviewers to provide feedback.
*   **Tips for successful PRs:**
    *   Write clear and concise code.
    *   Follow the code style guidelines.
    *   Write tests for your changes.
    *   Provide a clear description of your changes.
    *   Be responsive to feedback.

## Code Review

Code review is an essential part of the development process. Here's what reviewers will be looking for:

*   **Acceptance Criteria:**
    *   Code follows the code style guidelines.
    *   Code is well-documented.
    *   Code is tested.
    *   Code addresses the issue or feature request.
*   **What the reviewer looks for:**
    *   Code correctness.
    *   Code readability.
    *   Code maintainability.
    *   Code performance.
*   **How to receive feedback:** Be open to feedback and willing to make changes.
*   **How to do follow-up:** Address all feedback and make necessary changes.

## Documentation

Documenting your changes is crucial for making the project accessible and understandable.

*   **How to document changes:** Update the documentation to reflect any changes you've made to the code.
*   **Where to document:**
    *   Update docstrings for functions and classes.
    *   Update the README file.
    *   Add new documentation files if necessary.
*   **Examples in docstrings:**
    ```python
    def my_function(arg1: str, arg2: int) -> bool:
        """
        This function does something.

        Args:
            arg1: The first argument.
            arg2: The second argument.

        Returns:
            True if the function succeeds, False otherwise.
        """
        # ...
    ```
*   **README updates:** Update the README file with any new features or changes to the project.

## Recognition

We appreciate all contributions to profesores and want to recognize your efforts.

*   **How contributors are recognized:**
    *   Your name will be added to the list of contributors in the README file.
    *   Your contributions will be mentioned in the release notes.
*   **List of contributors:** See the README file for a list of contributors.
*   **Credits in release notes:** Your contributions will be credited in the release notes for each release.

## Contact and Questions

If you have any questions or need help, please don't hesitate to contact us.

*   **Email for questions:** [Maintainer's Email Address]
*   **Discord/Slack community:** [Link to Discord/Slack Community, if applicable]
*   **Discussions on GitHub:** [Link to GitHub Discussions, if enabled]
*   **Maintainer's Email:** [Maintainer's Email Address]
```