# AI Model Design for ShopEase

## 1. What are the features?

The features would include the ticket title, full customer message,
customer-selected category, submission time, urgency-related words,
device type, app version, previous support tickets, recent order or
payment status, and the number of similar recent tickets.


## 2. What is the label?

The main label is the correct support category such as Account Access,
Payment Problem, Order Problem, Technical Error, Feature Request, or
Other Issue. Another label is Urgent or Not Urgent.


## 3. What would training data contain?

The training data would contain past ShopEase support tickets with
their titles, messages, useful ticket information, final
employee-selected category, and urgency label.


## 4. Why should testing data be kept separate?

Testing data should be kept separate so we can check whether the model
works well on new tickets it has not seen before, instead of only
memorizing the training data.


## 5. What could be a false positive?

A normal ticket is incorrectly marked as urgent.


## 6. What could be a false negative?

An actually urgent ticket is incorrectly marked as not urgent.


## 7. Would precision or recall be more important?

Recall would be more important for urgent tickets.

Missing a real urgent problem could have a bigger impact than checking
a few extra tickets that were incorrectly marked urgent.


## 8. What types of poor-quality data could affect this model?

Missing ticket information, unclear messages, wrong categories,
inconsistent employee decisions, duplicate tickets, and outdated app
or device information.


## 9. What could cause this model to overfit?

The model could overfit if it learns specific training tickets or
certain words too closely instead of learning general patterns that
also work for new tickets.


## 10. What would make you trust—or not trust—the model's predictions?

I would trust it more if it performs well on separate testing data and
has good accuracy, precision, and recall. I would trust it less if it
often sends tickets to the wrong team or misses urgent problems. An
employee should still review the model's suggestion.
