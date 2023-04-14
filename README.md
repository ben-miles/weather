# weather

A simple weather app, powered by Vue 3 and OpenWeatherMap, with ultra-lightweight SVG graphics and icons.

[![Vue](https://img.shields.io/badge/Vue%203-green?style=for-the-badge&logo=vuedotjs&logoColor=white)](https://vuejs.org/)
[![Vite](https://img.shields.io/badge/Vite-B73BFE?style=for-the-badge&logo=vite&logoColor=FFD62E)](https://vitejs.dev/)
[![Github Actions](https://img.shields.io/badge/Github%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)](https://github.com/features/actions)
[![Github Pages](https://img.shields.io/badge/Github%20Pages-2088FF?style=for-the-badge&logo=githubpages&logoColor=white)](https://pages.github.com/)

## Live Demo

- You can see a live demo at [htps://ben-miles.github.io/weather/](https://ben-miles.github.io/weather/).

## Installation

1. Clone this repository and provision a web server for the project.
2. Make sure [Node.js](https://nodejs.org) and [NPM](https://www.npmjs.com) are installed.
3. To work with this app locally, you'll first need an API Key from [OpenWeatherMap](https://openweathermap.org). 
4. In the project root, create a copy of `.env-example`, rename it to `.env`, and replace the placeholder value of `VITE_OPENWEATHERMAP_KEY` with your API Key.
5. In the project's root directory, run `npm install` in the terminal.

## Development

- It's recommended to use [VSCode](https://code.visualstudio.com/) with the [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) extension.
- For a live preview of the source code, run `npm run dev`.

## Deployment

- This repo uses GitHub Actions (with [this Workflow by Vite](https://vitejs.dev/guide/static-deploy.html#github-pages)) to automatically build and deploy to GitHub Pages whenever new code is pushed to the `master` branch. 
- You can also build locally by running `npm run build`, and you can preview that build with `npm run preview`.
