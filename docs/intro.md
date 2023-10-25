---
sidebar_position: 1
slug: /
---

## Getting Started

Please refer: [Docs](https://docusaurus.io/docs) for initial start.

Get started by **creating a new site**.

Go to you Github

  1. Create new repository.
  2. fill repository name that you like.
      *Please remember ``your repository name``.

### What you'll need

- [Node.js](https://nodejs.org/en/download/) version 16.14 or above:
  - When installing Node.js, you are recommended to check all checkboxes related to dependencies.

## Generate a new site

Generate a new Docusaurus site using the **classic template**.

The classic template will automatically be added to your project after you run the command:

```bash
npm init docusaurus@latest <your repository name> classic
```

You can type this command into Command Prompt, Powershell, Terminal, or any other integrated terminal of your code editor.

The command also installs all necessary dependencies you need to run Docusaurus.

## Start your site

Run the development server:

```bash
cd <your repository name>
npm install
```

## Manage your site

Edit docusaurus.config.js file to index to you Github repository.

```jsx title="docusaurus.config.js"

const lightCodeTheme = require('prism-react-renderer/themes/github');
const darkCodeTheme = require('prism-react-renderer/themes/dracula');

/** @type {import('@docusaurus/types').Config} */
const config = {
  title: 'My Site',  // Your Website name
  tagline: 'Dinosaurs are cool',  // It's can be blank
  favicon: 'img/favicon.ico',  // You can change favicon icon in /static/img

  url: 'https://github.com',  // Always use github.com ***don't put / after github.com
  baseUrl: '/<your repository name>/',   // For GitHub pages deployment, it is often '/<your repository name>/' ***don't forget "/" after. 

  organizationName: '<github user>', // Usually your GitHub org/user name.
  projectName: '<your repository name>', // Usually your repo name.
  deploymentBranch: "gh-pages",  // Add this line for Github pages deployment.

  onBrokenLinks: 'throw',
  onBrokenMarkdownLinks: 'warn',

  // Even if you don't use internalization, you can use this field to set useful
   i18n: {
    defaultLocale: 'en',
    locales: ['en'],
  },

  presets: [
    [
      'classic',
      /** @type {import('@docusaurus/preset-classic').Options} */
      ({
        docs: {
          sidebarPath: require.resolve('./sidebars.js'),
          // Please change this to your repo.
          // Remove this to remove the "edit this page" links.
          editUrl:
            'https://github.com/facebook/docusaurus/tree/main/packages/create-docusaurus/templates/shared/',
        },
        blog: {
          showReadingTime: true,
          // Please change this to your repo.
          // Remove this to remove the "edit this page" links.
          editUrl:
            'https://github.com/facebook/docusaurus/tree/main/packages/create-docusaurus/templates/shared/',
        },
        theme: {
          customCss: require.resolve('./src/css/custom.css'),
        },
      }),
    ],
  ],

  themeConfig:
    /** @type {import('@docusaurus/preset-classic').ThemeConfig} */
    ({
      // Add docs:{...} for auto collapse side menu.
      docs: {
        sidebar: {
          autoCollapseCategories: true,
          hideable: true,
        },
	    },
      // Add colorMode:{...} to set dark mode as default.
      colorMode: {
        defaultMode: 'dark',
        disableSwitch: false,
        respectPrefersColorScheme: false,
      },
      image: 'img/docusaurus-social-card.jpg', // You can delete this line.
      navbar: {
        title: 'My Site',  // Your site name that will show at top left.
        logo: {
          alt: 'My Site Logo',
          src: 'img/logo.svg',  // Your site name that will show at top left (/static/img).
          target: '_self',
        },
        items: [
          // Add /* */ to hide Tutorial and Blog menu
         /* {
            type: 'docSidebar',
            sidebarId: 'tutorialSidebar',
            position: 'left',
            label: 'Tutorial',
          },
          {to: '/blog', label: 'Blog', position: 'left'},*/
          {
            href: 'https://github.com/facebook/docusaurus', // Change to your github link.
            label: 'GitHub',
            position: 'right',
          },
        ],
      },
      footer: {
        style: 'dark',
        // Add /* */ to hide footer menu
        /*links: [
          {
            title: 'Docs',
            items: [
              {
                label: 'Tutorial',
                to: '/docs/intro',
              },
            ],
          },
          {
            title: 'Community',
            items: [
              {
                label: 'Stack Overflow',
                href: 'https://stackoverflow.com/questions/tagged/docusaurus',
              },
              {
                label: 'Discord',
                href: 'https://discordapp.com/invite/docusaurus',
              },
              {
                label: 'Twitter',
                href: 'https://twitter.com/docusaurus',
              },
            ],
          },
          {
            title: 'More',
            items: [
              {
                label: 'Blog',
                to: '/blog',
              },
              {
                label: 'GitHub',
                href: 'https://github.com/facebook/docusaurus',
              },
            ],
          },
        ],*/
        copyright: `Copyright © ${new Date().getFullYear()} Nutanix Thailand. Built with Docusaurus.`,  // Change to your organization name.
      },
      prism: {
        theme: lightCodeTheme,
        darkTheme: darkCodeTheme,
      },
    }),
};

module.exports = config;

```

1. Initial Github
    ```bash titel=""
        git init
    ```

2. Add every things to Github
    ```bash titel=""
        git add .
    ```

3. Commit to Github with message `fist commit`
    ```bash titel=""
        git commit -m 'first commit'
    ```

4. Select `main` branch
    ```bash titel=""
        git branch -M main
    ```

5. Remote to your Github repository
    ```bash titel=""
        git remote add origin https://github.com/<your Github user>/<your repository>.git
        ### Replace with your Github user and your repository.
    ```

6. Push every things to your repository at `main` branch.
    ```bash titel=""
        git push -u original main
    ```

7. Deploy website to your Github repository.
    <Tabs groupId="deploy">
    <TabItem value="kubeconfig file" label="PowerShell">

    ```bash title="Please change your Github username"
    cmd /C 'set "GIT_USER=<GITHUB_USERNAME>" && yarn deploy'
    ```

    </TabItem>
    <TabItem value="" label="Bash">

    ```bash title="Please change your Github username"
    GIT_USER=<GITHUB_USERNAME> yarn deploy
    ```

    </TabItem>
    </Tabs>

8. Create Github pipeline for deployment.
    ```bash titel=""
        mkdir .github
    ```

9. Create `workflows` directory under `.github`.
    ```bash titel=""
        mkdir .github/workflows
    ```

10. Create `deploy.yml` for github pages deployment with VSC.

    ![](/static/img/create_deploy.png)

11. Copy all in bellow box to `deploy.yml` then edit some lines.

    ```jsx titel="deploy.yml"
        name: Deploy to GitHub Pages

        on:
          push:
            branches:
              - main
            paths:
              - <your repository>/**  ## << Change to your Github repository.
            # Review gh actions docs if you want to further define triggers, paths, etc
            # https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#on

        permissions:
          contents: write

        jobs:
          deploy:
            name: Deploy to GitHub Pages
            runs-on: ubuntu-latest
            steps:
              - uses: actions/checkout@v3
              - uses: actions/setup-node@v3
                with:
                  node-version: 18
                  cache: yarn

              - name: Install dependencies
                run: yarn install --frozen-lockfile
              - name: Build website
                working-directory: <your repository>    ## << Change to your Github repository.
                run: yarn build

              # Popular action to deploy to GitHub Pages:
              # Docs: https://github.com/peaceiris/actions-gh-pages#%EF%B8%8F-docusaurus
              - name: Deploy to GitHub Pages
                uses: peaceiris/actions-gh-pages@v3
                with:
                  github_token: ${{ secrets.GITHUB_TOKEN }}
                  # Build output to publish to the `gh-pages` branch:
                  publish_dir: ./<your repository>/build                      ############### << Change to your Github repository.
                  # The following lines assign commit authorship to the official
                  # GH-Actions bot for deploys to `gh-pages` branch:
                  # https://github.com/actions/checkout/issues/13#issuecomment-724415212
                  # The GH actions bot is used by default if you didn't specify the two fields.
                  # You can swap them out with your own user credentials.
                  user_name: github-actions[bot]
                  user_email: 41898282+github-actions[bot]@users.noreply.github.com
    ```

12. Make `intro.md` to be landing page.

    ```jsx  titel="docs/intro.md"
    ---
    sidebar_position: 1
    slug: /  // Add this line to make this file be /root path.
    ---

    ```

13. Remove /src/pages/index.js

    ![](/static/img/delete_index.png)


## Check your Github pages website



The `cd` command changes the directory you're working with. In order to work with your newly created Docusaurus site, you'll need to navigate the terminal there.

The `npm run start` command builds your website locally and serves it through a development server, ready for you to view at http://localhost:3000/.

Open `docs/intro.md` (this page) and edit some lines: the site **reloads automatically** and displays your changes.
