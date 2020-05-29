Consider a function that is subscribed to messages on a queue and is performing some tasks that are subject to a number of time-sensitive business constraints.
Thus, for a particular invocation, the function may determine that it cannot process a message at the current time. 
Currently, the lambda function must raise an error to ensure that the message remains on the queue, and can be processed at a later point in time.
There is currently no mechanism to distinguish between such routine "errors" and errors from execution issues.
All errors are "black" in monitoring
