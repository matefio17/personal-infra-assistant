# Contributing Guidelines



Thank you for taking an interest in the **AI Personal Infrastructure Assistant**. Even though this project is primarily my personal learning sandbox, maintaining high-quality code, consistent workflow standards, and professional git discipline is a core part of the learning experience.



To keep the repository clean, structured, and professional, please adhere to the guidelines outlined below.



---



##  Branching Strategy & Workflow



We follow a simplified Git-Flow / Feature-Branch workflow to keep the `main` branch stable and ready for deployment at all times.



1.  **Do not commit directly to the `main` branch**.

2.  Create a new branch for every task, feature, or bug fix.

3.  Name branches using the following prefixes:

&#x20;   *   `feature/` - for new features or extensions (e.g., `feature/setup-backend`).

&#x20;   *   `bugfix/` - for correcting issues in existing code.

&#x20;   *   `docs/` - for documentation updates.

&#x20;   *   `chore/` - for configurations, tooling, and general maintenance.

4.  Push your branch to GitHub and open a **Pull Request (PR)** to merge into `main`.



---



##  Conventional Commits Specification



Using this convention makes our git history highly readable and allows us to automate our release cycles and changelog generation later in the roadmap.



### Commit Message Format



Each commit message must consist of a **header** (containing a **type**, an optional **scope**, and a **description**):



```text

<type>(<scope>): <description>



```



### Commit Types



* **`feat`**: A new feature added to the codebase (e.g., `feat(agent): add disk smart diagnostics`).





* **`fix`**: A bug fix (e.g., `fix(backend): resolve token expiration crash`).





* **`docs`**: Documentation only changes (e.g., `docs: add contributing guide`).





* **`chore`**: Updates to build tasks, package manager configs, or developer tools (e.g., `chore: setup editorconfig`).





* **`refactor`**: A code change that neither fixes a bug nor adds a feature (e.g., `refactor(backend): modularize user routers`).





* **`style`**: Changes that do not affect the meaning of the code (white-space, formatting, etc.).





* **`test`**: Adding missing tests or correcting existing ones (e.g., `test(backend): add authentication unit tests`).





* **`perf`**: A code change that improves performance.



### Rules & Best Practices



1. **Use the imperative mood** in the description (e.g., use "add" instead of "added" or "adds").





2. **Do not capitalize** the first letter of the description.





3. **No period (`.`)** at the end of the commit message.





4. Keep the header under **50 characters** if possible.







---



##  Pull Request Process



To ensure that changes are reviewed and tested before reaching `main`, follow these steps:



1. **Self-Review**: Before submitting, look at your own diff. Ensure there are no leftover debuggers or temporary comments.





2. **Lint & Format**: Ensure your code complies with the project's `.editorconfig` rules.





3. **Write Description**: Briefly explain what changes were made and why, referencing the corresponding GitHub Project card.





4. Once all status checks are green, the PR can be safely merged into `main`.



