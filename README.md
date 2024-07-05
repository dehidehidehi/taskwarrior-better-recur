# Better Recurring Tasks for CodeWarrior
(c) 2024 by [Scott O'Brien](https://www.scottyob.com/), MIT License

## Installation
task config uda.relativeRecurDue.type duration
task config uda.relativeRecurDue.label 'Rel. Rec. Due'
task config uda.relativeRecurWait.type duration
task config uda.relativeRecurWait.label 'Rel. Rec. Wait'
task config uda.expires.type string
task config uda.expires.label 'Expires'
task config uda.completeRecurDue.type string
task config uda.completeRecurDue.label 'Com. Rec. Due'
task config uda.completeRecurWait.type string
task config uda.completeRecurWait.label 'Com. Rec. Wait'


## Relative Recurring Usage
You shouldn't mow your lawn more than once a week, but want to keep it short, so shouldn't wait for more than two weeks:
```
task add 'Mow the Lawn' relativeRecurWait:1weeks relativeRecurDue:2weeks
```

## Expiring Recursive Task Usage
The bins need to go out every week at Sunday, but, if you missed them by 10am, then the truck has probably already come, and you can try again the next week
```
task add 'Take the bins out' due:Monday wait:due-1d recur:weekly expires:10h
```

## Wait and Due "on complete"
The dishes need to be done every night, once they're done (completed), we'll want to schedule it for tomorrow.  You can always push this task off to stop it from re-firing
```
task add 'Do the dishes' completeRecurWait:"tomorrow +17hours" completeRecurDue:"tomorrow +1day"
```
