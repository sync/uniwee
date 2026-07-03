# Uniwee

Uniwee is a pnpm monorepo with two React Native apps:

- `apps/rn-app`: a plain React Native CLI app.
- `apps/expo-app`: an Expo app.

## Getting Started

Use the Node version from `.node-version`, then install dependencies from the repo root:

```sh
pnpm i
```

This repo is configured for `pnpm@10.33.2`. Use pnpm for installs so workspace
dependencies and package patches are applied correctly.

The workspace apps live under `apps/*`. Root scripts are available for starting
Metro, and app-specific commands can be run with `pnpm --filter <app-name> <script>`.

## Expo App

The Expo app lives in `apps/expo-app`.

Start Metro:

```sh
pnpm start:expo
```

Prepare native projects:

```sh
pnpm --filter expo-app prebuild
```

Run the app:

```sh
pnpm --filter expo-app ios
pnpm --filter expo-app android
```

## React Native App

The plain React Native app lives in `apps/rn-app`.

Start Metro:

```sh
pnpm start:rn
```

Install native iOS dependencies:

```sh
pnpm --filter rn-app prebuild
```

Run the app:

```sh
pnpm --filter rn-app ios
pnpm --filter rn-app android
```

Run checks:

```sh
pnpm --filter rn-app lint
pnpm --filter rn-app test
```

## Notes

- Run Metro in one terminal and the iOS or Android command in another.
- Both Metro scripts use the default Metro port behavior. Do not run both Metro
  servers at the same time unless you configure one of them to use a different port.
- Both apps use Uniwind and Tailwind through each app's `global.css`.
- The repo includes a pnpm patch for `uniwind@1.10.0`, so use pnpm instead of npm
  or yarn.
