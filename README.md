##  Prepare Your Project
Create a New Directory:
```
mkdir my-npm-package
cd my-npm-package
```
## Initialize npm:
```
npm init -y
```
This will create a package.json file.

## Add Your Code:
Create a index.js file:
```
touch index.js
```

Add your module logic:
```
// index.js
module.exports = function greet(name) {
  return `Hello, ${name}!`;
};
```
## Configure package.json for GitHub Registry:

* Add the repository field:
```
"repository": {
  "type": "git",
  "url": "https://github.com/<your-username>/<your-repo>.git"
}
```
Set the publishConfig to GitHub's registry:
```
"publishConfig": {
  "registry": "https://npm.pkg.github.com"
}
```
Ensure the name is scoped with your GitHub username:
```
"name": "@<your-username>/my-npm-package"
```
## Push Your Code to a Public GitHub Repository
Create a GitHub Repository:

Go to GitHub and create a repository named my-npm-package.
Initialize Git and Push Your Code:

```
git init
git remote add origin https://github.com/<your-username>/my-npm-package.git
git branch -M main
git add .
git commit -m "Initial commit"
git push -u origin main
```
## Authenticate with GitHub Registry
Generate a Personal Access Token (PAT):
- Go to your GitHub Developer Settings.
- Generate a token with `write:packages`, `read:packages`, and `repo` scopes.
- Save the token for the next step.
- Authenticate npm to Use GitHub Registry:
```
npm login --registry=https://npm.pkg.github.com
```

- Username: Your GitHub username.
- Password: Your PAT (Personal Access Token).
- Email: Your GitHub-associated email.
##
Publish the Package
Run the following command to publish the package to the GitHub Package Registry:
```
npm publish
```
## Consume the Package
Add the GitHub Registry in your project's .npmrc file:
```
echo "@<your-username>:registry=https://npm.pkg.github.com" >> .npmrc
```
## Install your package in a project:
```
npm install @<your-username>/my-npm-package
```
Use it in your project:

```
const greet = require('@<your-username>/my-npm-package');
console.log(greet('World')); // Output: Hello, World!
```
## Update the Package
Make changes to your code.
Bump the version in package.json:
```
npm version patch
```
## Publish the updated package:
```
npm publish
``` 