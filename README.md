## Instructions

1. **Fork the Repository:**
   - Go to the GitHub page of the repository.
   - Click on the "Fork" button at the top right corner of the page to create a copy of the repository under your GitHub account.

2. **Clone the Forked Repository:**
   - Open your terminal.
   - Use the following command to clone the forked repository to your local machine:
     ```bash
     git clone https://github.com/YOUR_GITHUB_USERNAME/YOUR_REPOSITORY_NAME.git
     ```
   - Replace `YOUR_GITHUB_USERNAME` with your GitHub username and `YOUR_REPOSITORY_NAME` with the name of the repository you just forked.

3. **Navigate to the Repository Directory:**
   - Change into the directory of the cloned repository:
     ```bash
     cd FOLDER/REPOSITORY_NAME
     ```

4. **Set Up Remote to Track Original Repository:**
   - Add the original repository as a remote named `upstream`:
     ```bash
     git remote add upstream https://github.com/gojandrooo/4ga-supplemental.git
     ```
    - this will make it easy to get new files as they are added throughout the course

## Keeping Your Fork Updated

To keep your fork updated with the latest changes from the original repository without overwriting your work, follow these steps:

1. **Fetch the Latest Changes from Upstream:**
   - Fetch the latest changes from the original repository:
     ```bash
     git fetch upstream
     ```

2. **Create a New Branch for Merging:**
   - Create a new branch to merge the changes from upstream:
     ```bash
     git checkout -b merge-upstream
     ```

3. **Merge the Changes into the New Branch:**
   - Merge the changes from the `main` branch of the original repository into your new branch:
     ```bash
     git merge upstream/main
     ```

4. **Resolve Any Merge Conflicts:**
   - If there are any merge conflicts, Git will prompt you to resolve them. Open the conflicting files, make the necessary changes, and then commit the resolved files:
     ```bash
     git add <resolved_file>
     git commit
     ```

5. **Switch Back to Your Main Branch:**
   - Switch back to your main branch:
     ```bash
     git checkout main
     ```

6. **Merge the New Branch into Your Main Branch:**
   - Merge the new branch into your main branch:
     ```bash
     git merge merge-upstream
     ```

7. **Push the Updates to Your Fork:**
   - Push the merged changes to your forked repository on GitHub:
     ```bash
     git push origin main
     ```

## Best Practices for Managing Changes

- **Commit Regularly:** Regularly commit your changes to avoid losing work and to make it easier to resolve conflicts.
- **Use Branches:** Create branches for new features or experiments to keep your main branch clean and stable.
  ```bash
  git checkout -b new-feature-branch