# Better Recurring Tasks for CodeWarrior

Originally by:
- (c) 2024 by [Scott O'Brien](https://www.scottyob.com/), MIT License

## Installation

1. Place the scripts from this repository in the `~/.task/hooks/` dir.
1. Add the following to your `taskrc` file.

```
uda.rdue.type=duration
uda.rdue.label='Rel. Rec. Due'
uda.rwait.type=duration
uda.rwait.label='Rel. Rec. Wait'
uda.expires.type=string
uda.expires.label='Expires'
uda.crdue.type=string
uda.crdue.label='Com. Rec. Due'
uda.crwait.type=string
uda.crwait.label='Com. Rec. Wait'
```

## Relative Recurring Usage
You shouldn't mow your lawn more than once a week, but want to keep it short, so shouldn't wait for more than two weeks:
```
task add 'Mow the Lawn' rwait:1weeks rdue:2weeks
```

## Expiring Recursive Task Usage
The bins need to go out every week at Sunday, but, if you missed them by 10am, then the truck has probably already come, and you can try again the next week
```
task add 'Take the bins out' due:Monday wait:due-1d recur:weekly expires:10h
```

## Wait and Due "on complete"
The dishes need to be done every night, once they're done (completed), we'll want to schedule it for tomorrow.  You can always push this task off to stop it from re-firing
```
task add 'Do the dishes' crwait:"tomorrow +17hours" crdue:"tomorrow +1day"
```

