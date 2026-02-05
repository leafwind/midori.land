# Sync upstream-main-deployable with upstream-main

## Resolve yarn.lock

```
git co upstream-main-deployable
git rebase -i upstream-main
git checkout --theirs yarn.lock
git add yarn.lock
```

## Remove unused packages

Add these lines back temporary to `package.json`

```
"@atproto/dev-env": "^0.3.206",
"expo-dev-client": "~6.0.20",
```

Then remove them:

```
yarn remove @atproto/dev-env
yarn remove expo-dev-client
```

Delete cache and reinstall all packages:

```
rm -rf node_modules/
yarn install --frozen-lockfile
```

## Continue rebase

```
git a
git rebase --continue
git push origin upstream-main-deployable -f
```

