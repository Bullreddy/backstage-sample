# [Backstage](https://backstage.io)

This is your newly scaffolded Backstage App, Good Luck!

To start the app, run:

```sh
yarn install
yarn dev
```


Github and Google sign in Provider Implementation

Backend

create auth module for google and github provider with signin resolver to reolve user from post login response from Provider
packages/backend/src/authModuleGoogleProvider.ts
packages/backend/src/authModuleGithubProvider.ts

add above auth Module for github and google provider as backend module
in packages/backend/src/index.js
add below lines

backend.add(import('./authModuleGithubProvider'))
backend.add(import('./authModuleGoogleProvider'));

Frontend
Adding the Google and Github provider to the Backstage frontend

in file packages\app\src\App.tsx

add below code
import { githubAuthApiRef,googleAuthApiRef } from '@backstage/core-plugin-api';

export const providers = [
  {
    id: 'github-auth-provider',
    title: 'GitHub',
    message: 'Sign In using GitHub',
    apiRef: githubAuthApiRef,
  },
  {
    id: 'google-auth-provider',
    title: 'Google',
    message: 'Sign In using Google',
    apiRef: googleAuthApiRef,
  },
]

in app-config.yaml file
add config for google and github under auth->providers as below
ClientID and Client Secret to be obtained from respective provider Config
auth:
  providers:
    guest: {}
    google:
      development:
        clientId: ******************************.apps.googleusercontent.com
        clientSecret: ****************************
        signIn:
          resolvers:
            - resolver: emailMatchingUserEntityProfileEmail
    github:
      development:
        clientId: **********************
        clientSecret: **************************

