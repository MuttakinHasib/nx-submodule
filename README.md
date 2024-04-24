# NX Monorepo with submodule

## Installation guide

1) Open terminal and enter the following command:
   1) `npx create-nx-workspace@latest`
   2) Where would you like to create your workspace? &rarr; `project-name`
   3) Which stack do you want to use? &rarr; `React`
   4) What framework would you like to use? &rarr; `Next.js`
   5) Integrated monorepo, or standalone project? &rarr; `Integrated Monorepo:...`
   6) Application name? &rarr; `public-app`
   7) Would you like to use the App Router (recommended)? &rarr; `Yes`
   8) Would you like to use the src/ directory? &rarr; `Yes`
   9) Would you like to use the src/ directory? &rarr; `Yes`
   10) Test runner to use for end to end (E2E) tests? &rarr; `None`
   11) Default stylesheet format? &rarr; `tailwind`
   12) Do you want Nx Cloud to make your CI fast? &rarr; `Yes, configure Nx Cloud for GitHub Actions`
   13) Do you want Nx Cloud to make your CI fast? &rarr; `Yes, configure Nx Cloud for GitHub Actions`

2) Open your created workspace with any code editor like `vscode`
3) Install NX Console extension on your vs code editor [NX Console](https://marketplace.visualstudio.com/items?itemName=nrwl.angular-console)
4) Now, generate a private app using **NX Console**
   1) Open Nx Console
   2) click on the `generate` button from the `Generate & Run Target` section of the Nx Console
   3) Now choose `@nx/next - application Create an application` and it will open a Generate UI tab on VS Code
   4) Fill up the required and optional fields based on your need. Here i am fill upping `name` `private-app`, `directory` &rarr; `apps/private-app`, `e2eTestRunner` &rarr; `none` and `unitTestRunner` &rarr; `none`
   5) Click on the `Generate` button and it will generate the application for you.

5) Now to the `package.json` file and add the following script:

    ```json
    "scripts": {
        "dev": "nx run-many --target=dev --all=true"
    },

    ```

6) Now run the command `npm run dev` and it will run the `dev` target for all the applications.

7) Now stop the server

## Let's make the private-app as private

1) Cut `private-app` from the `apps` folder and paste it in the outside of this nx workspace.
2) now git init & commit the `private-app` and push it to the github private repo.
3) Now go to your nx workspace (monorepo) and run the following commands:
   1) `git submodule add <URL-to-private-repo> apps/private-app`
   2) It will create a `.gitmodules` file in the root of the nx workspace.
   3) Go to the `.gitmodules` and just add this line after the `url` field &rarr; `branch = main`
   4) now commit your git and push it to a git repository.

Here is the nx-submodule link I have created: [NX Public Repo](https://github.com/MuttakinHasib/nx-submodule)

## Working with the Project
Developers with access can work with the submodule by initializing and updating it:

```bash
cd my-monorepo
git submodule update --init
```

Developers without access to the private app submodule will skip the submodule initialization and update steps.
