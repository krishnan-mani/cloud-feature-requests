### Summary

Lambda functions allow specifying a single handler.
This request seeks support for multiple handlers based upon, for example, matching the shape of the event in an invoication.

By doing so, it will be easier to split up and organise function code into smaller, more-focused parts that each perform a specific task well, with all of the consequent benefits.

### Rationale

A common pattern is a Lambda function subscribed to change events from a DynamoDB table. Change events may differ in terms of actions on the items, such as new items, updates to items, and deleted items.

The code that deals with each kind of event can be created, tested, and configured independently. Each unit of such code can have an independent handler that is configured per the event. 

Furthermore, a default handler can be optionally configured. (see enhancements for more)

#### Examples

# Acting on item changes in a DynamoDB table, based upon the change to items
# Acting on changes to files in an S3 bucket, based upon the event

#### Enhancements

# Configuring a default handler may be made optional (at some future point, since existing Lambda functions require one)
# When made optional, and if the service is unable to determine an appropriate handler to invoke, invocations may follow the established error-handling semantics.
# Provide monitoring that helps determine which handlers are invoked and how often
