# 3 ways to deploy Web Apss to Netlify

Main reference: [3 ways to deploy Web Apss to Netlify](https://youtu.be/MEIMoz9pGRM) 2021

## Install. Use node v16!

```
three-ways-to-deploy npm i @vue/cli@4.5.9
 npm i @vue/cli@4.5.9
npm ERR! code EBADENGINE
npm ERR! engine Unsupported engine
➜  three-ways-to-deploy node --version
v18.8.0
➜  three-ways-to-deploy nvm use v16
Now using node v16.0.0 (npm v8.3.2)
➜  three-ways-to-deploy npm i @vue/cli@4.5.9
npm WARN deprecated source-map-url@0.4.1: See https://github.com/lydell/source-map-url#deprecated
# ... lots of deprecated ... messages
added 967 packages, and audited 989 packages in 12s
```

## "vue create netlify-demo" and errors I committed during the installation


```
➜  three-ways-to-deploy git:(main) vue create netlify-demo
```

Accept all defaults

### Errors I committed during the installation


**Am I running a global vue-cli or a local one?**

```
➜  three-ways-to-deploy git:(main) ✗ nvm use      
Found '/Users/casianorodriguezleon/campus-virtual/2223/learning/netlify-learning/brain-morrison-videos/three-ways-to-deploy/.nvmrc' with version <v16>
Now using node v16.0.0 (npm v8.3.2)
➜  three-ways-to-deploy git:(main) ✗ vue --version 
@vue/cli 4.5.15
➜  three-ways-to-deploy git:(main) ✗ npx vue --version
@vue/cli 4.5.9
```

Not much difference. I will continue with the global one:

```
➜  three-ways-to-deploy git:(main) ✗ npm uninstall  @vue/cli@4.5.9
```

## Running in development mode

```
➜  three-ways-to-deploy git:(main) ✗ cd netlify-demo 
➜  netlify-demo git:(main) ✗ npm run serve

> netlify-demo@0.1.0 serve
> vue-cli-service serve

 INFO  Starting development server...
98% after emitting CopyPlugin

 DONE  Compiled successfully in 2341ms                                                        9:19:23


  App running at:
  - Local:   http://localhost:8081/ 
  - Network: http://192.168.1.235:8081/

  Note that the development build is not optimized.
  To create a production build, run npm run build.
  ```

  Everything is working fine. I can see the app in the browser.

  ## npm run build

  ```
  ➜  netlify-demo git:(main) ✗ npm run build

> netlify-demo@0.1.0 build
> vue-cli-service build


⠴  Building for production...

 DONE  Compiled successfully in 3968ms                                                        9:21:30

  File                                 Size                          Gzipped

  dist/js/chunk-vendors.caf87120.js    70.67 KiB                     25.41 KiB
  dist/js/app.80f58bf0.js              4.40 KiB                      1.59 KiB
  dist/css/app.fb0c6e1c.css            0.33 KiB                      0.23 KiB

  Images and other types of assets omitted.

 DONE  Build complete. The dist directory is ready to be deployed.
 INFO  Check out deployment instructions at https://cli.vuejs.org/guide/deployment.html
 ``` 

## Manually Deploying to Netlify

**Minutes**: 3:17

1. Go to [Netlify](https://www.netlify.com/) and create an account.
2. Then visit **Team overview > Sites** and go to the end  of the menu

![Netlify manually installing 1](docs/images/manually-installing-1.png)

In the terminal open your file explorer:
  
```
➜  netlify-demo open .
``` 

and drag and drop the `dist` folder to the browser.

![Netlify manually installing 2](docs/images/manually-installing-2.png)

## Deployment through GitHub

**Minutes**: 4:05

```
➜  netlify-demo git init .
Inicializado repositorio Git vacío en /Users/casianorodriguezleon/campus-virtual/2223/learning/netlify-learning/brain-morrison-videos/three-ways-to-deploy/netlify-demo/.git/
➜  netlify-demo git:(main) ✗ git status
En la rama main

No hay commits todavía

Archivos sin seguimiento:
  (usa "git add <archivo>..." para incluirlo a lo que será confirmado)
        .gitignore
        .nvmrc
        README.md
        babel.config.js
        docs/
        package-lock.json
        package.json
        public/
        src/

no hay nada agregado al commit pero hay archivos sin seguimiento presentes (usa "git add" para hacerles seguimiento)
➜  netlify-demo git:(main) ✗ git add .
➜  netlify-demo git:(main) ✗ git ci -am 'reparing for deploy to netlify' 
[main (commit-raíz) 213b6bc] reparing for deploy to netlify
 14 files changed, 28800 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 .nvmrc
 create mode 100644 README.md
 create mode 100644 babel.config.js
 create mode 100644 docs/images/manually-installing-1.png
 create mode 100644 docs/images/manually-installing-2.png
 create mode 100644 package-lock.json
 create mode 100644 package.json
 create mode 100644 public/favicon.ico
 create mode 100644 public/index.html
 create mode 100644 src/App.vue
 create mode 100644 src/assets/logo.png
 create mode 100644 src/components/HelloWorld.vue
 create mode 100644 src/main.js
➜  netlify-demo git:(main) gh repo create
? What would you like to do? Push an existing local repository to GitHub
? Path to local repository .
? Repository name ULL-MII-SYTWS/brian-morrison-on-netlify
? Description https://youtu.be/MEIMoz9pGRM
? Visibility Public
✓ Created repository ULL-MII-SYTWS/brian-morrison-on-netlify on GitHub
? Add a remote? Yes
? What should the new remote be called? origin
✓ Added remote git@github.com:ULL-MII-SYTWS/brian-morrison-on-netlify.git
? Would you like to push commits from the current branch to "origin"? Yes
Enumerando objetos: 22, listo.
Contando objetos: 100% (22/22), listo.
Compresión delta usando hasta 8 hilos
Comprimiendo objetos: 100% (18/18), listo.
Escribiendo objetos: 100% (22/22), 579.60 KiB | 4.17 MiB/s, listo.
Total 22 (delta 0), reusados 0 (delta 0), pack-reusados 0
To github.com:ULL-MII-SYTWS/brian-morrison-on-netlify.git
 * [new branch]      HEAD -> main
rama 'main' configurada para rastrear 'origin/main'.
✓ Pushed commits to git@github.com:ULL-MII-SYTWS/brian-morrison-on-netlify.git
```

![Netlify GitHub 1](docs/images/github-installing-1.png)

![Netlify GitHub 2](docs/images/github-installing-2.png)

![Netlify GitHub 3](docs/images/github-installing-3.png)