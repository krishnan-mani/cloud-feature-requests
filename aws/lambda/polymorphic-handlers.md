### Summary

Lambda functions currently allow specifying a single handler method.
This feature request seeks support for multiple handlers based upon, say, matching the shape of the event in an invoication.

As a customer, I use a single Lambda function to respond to a particular source of events (say, messages on a queue, or a change stream from a DynamoDB table). However, even a single source of events can consist of different kinds of events. As the code and tests are organised around the handler function, by making it possible to use multiple handler functions, the code to respond to different kinds of events can be organised in a more focussed manner.

### Rationale

A common pattern is a Lambda function subscribed to change events from a DynamoDB table. Change events may differ in terms of actions on the items, such as new items, updates to items, and deleted items.

The code that deals with each kind of event can be created, tested, and configured independently. Each unit of such code can have an independent handler that is configured per the event. 

Furthermore, a default handler can be optionally configured. (see enhancements for more)

#### Examples

- Acting on item changes in a DynamoDB table, based upon the change to items
- Acting on changes to files in an S3 bucket, based upon the event

#### Enhancements

- Configuring a default handler may be made optional (at some future point, since existing Lambda functions require one)
- When made optional, and if the service is unable to determine an appropriate handler to invoke, invocations may follow the established error-handling semantics.
- Provide monitoring that helps determine which handlers are invoked and how often
