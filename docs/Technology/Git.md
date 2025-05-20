---
title: Git
tags: tool
---

## Empty commit

Do an empty commit:

```bash
git commit --allow-empty -m "Trigger Build"
```

Push to trigger a build of a PR:

```bash
git push -f origin feat-branch-name
```

## Undo quickly

If quickly testing some unstaged changes on a file,
the changes can be undone with:

```bash
git checkout <file>
```

## Interactive add

Let's say you want to sync one file from upstream.

```bash
cp ../upstream/file.txt .
```

Now you want to selectively stage changes.
The best way is an interactive add:

```bash
git add -p file.txt
```

You can then say (n)o, (y)es or (d)iscard for specific hunks.
You can also (s)plit hunks for finer-graind control and (e)dit
to modify a change.
Be careful not to make changes that will result in different line
numbers, as this can get messy

## Fork and pull

Submitting a PR when it turns out you don't have write access...

Fork the repo that you probably should have forked to begin with.

Then add that as a remote (`myfork` is arbitrary):

```bash
git remote add myfork git@github.com:user/repo.git
```

Now set that as an upstream and push your branch:

```bash
git push --set-upstream myfork cool-new-feature
```

## TODO Stop tracking

Sometimes you want to stop tracking a file that is already tracked.
