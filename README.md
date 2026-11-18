# Branching on an Event Schedule

A small event-schedule project used to practise feature branches, fast-forward
merges, three-way merges and manual conflict resolution.

## Files
- `schedule.md`: the event schedule
- `speakers.md`: the speakers page (added on `feature/speakers`)

## 1. Feature branch
I created `feature/speakers` from the initial schedule commit and committed
`speakers.md` there (commit `8c747dd`, "Add speakers page").

## 2. Fast-forward merge
The integration branch had no new commits after `feature/speakers` was created,
so merging it only moved the branch pointer forward. No merge commit was
created and the history stayed linear.

## 3. Three-way merge with a conflict
I created two branches from the same commit, each editing the same keynote line
in `schedule.md`:
- `edit-time` (`53a1008`): `09:00 Keynote - Main Hall` -> `10:00 Keynote - Main Hall`
- `edit-room` (`2a575fe`): `09:00 Keynote - Main Hall` -> `09:00 Keynote - Auditorium`

`edit-time` merged as a fast-forward. Merging `edit-room` then needed a
three-way merge, because both branches had diverged from their common ancestor.
Git compared the two tips with that ancestor, and since both changed the same
line, it stopped with a conflict.

## 4. Conflict resolution (by hand)
Git marked the file like this:

    <<<<<<< HEAD
    10:00 Keynote - Main Hall
    =======
    09:00 Keynote - Auditorium
    >>>>>>> edit-room

I edited the file, kept both changes (new time and new room), removed all
marker lines, ran `git add schedule.md` and committed the merge as `ac6bdb3`.
Final line: `10:00 Keynote - Auditorium`

## Fast-forward vs three-way merge
| | Fast-forward | Three-way |
|---|---|---|
| When | Target branch has no new commits | Both branches have new commits |
| Merge commit | No | Yes (two parents) |
| History | Linear | Shows a merge point |
| Conflicts | Not possible | Possible if the same lines changed |
| Example here | `feature/speakers`, `edit-time` | `edit-room` |

## Commit history

    *   ac6bdb3 Merge edit-room: resolve keynote time/room conflict
    |\
    | * 2a575fe Move keynote to Auditorium
    * | 53a1008 Move keynote to 10:00
    |/
    * 8c747dd Add speakers page
    * 37f369a Add initial event schedule
    * b79a272 Initial commit

## How to reproduce

    git checkout -b feature/speakers
    # add speakers.md
    git add speakers.md && git commit -m "Add speakers page"
    git checkout <integration-branch> && git merge feature/speakers   # fast-forward

    git checkout -b edit-time && # change keynote to 10:00, commit
    git checkout -b edit-room <integration-branch> && # change room, commit
    git merge edit-time        # fast-forward
    git merge edit-room        # three-way merge, CONFLICT
    # edit schedule.md, remove markers, keep "10:00 Keynote - Auditorium"
    git add schedule.md && git commit
