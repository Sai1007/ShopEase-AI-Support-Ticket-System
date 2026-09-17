# Proposal: AI-Based Customer-Support Ticket Sorting for ShopEase


## Why I chose this problem

I wanted to choose a problem that was related to my computer science
major but was still simple to explain. I thought about problems that a
technology company may face every day. Customer-support tickets seemed
like a good example because websites and mobile apps receive many
different types of complaints. I created a small startup called
ShopEase for this assignment. My idea is to use AI to help its
employees organize support tickets without letting the AI make the
final decision.


## Part 1 - Understand the Business Problem

### 1. What is the business problem?

ShopEase is a small startup that runs an online shopping website and
mobile app. Customers send tickets about payment problems, account
access, missing orders, app errors, and feature requests. An employee
currently has to read every ticket and decide which support team should
receive it. This takes time, and a ticket may sometimes be sent to the
wrong team. ShopEase wants a system that can suggest a category and
point out tickets that may be urgent.

### 2. Why is this problem important to the organization?

ShopEase has a small support team, so employees should spend more time
solving problems and less time sorting messages. When a ticket goes to
the wrong team, another employee has to read it and transfer it again.
This makes the customer wait longer. Missing an urgent problem, such as
an incorrect charge or a locked account, could also make the customer
lose trust in the company. Better ticket sorting could make support
faster and help the startup manage more customers as it grows.

### 3. Who is affected by this problem?

- Customers who are waiting for help
- Customer-support employees who sort the tickets
- Technical and payment-support teams
- Senior employees who handle urgent problems
- Developers who receive bug reports and feature requests
- Managers and owners of ShopEase


## Why AI may be useful

A normal rule-based program could look for words such as payment,
password, or error. The problem is that customers can explain the same
issue in many different ways. For example, “I cannot sign in” and
“my password is not working” probably describe the same type of
problem. Machine learning could learn patterns from tickets that
employees sorted in the past. It could then suggest a category for a
new ticket, but an employee would still check the result.


## Part 2 - Identify the Data

### What data would be needed?

ShopEase would need past ticket titles and messages, the category
selected by the customer, the final category selected by an employee,
and whether the ticket was urgent. Other useful information could
include the submission time, device type, app version, recent order or
payment status, and how the problem was resolved.

### Where could the data come from?

Most of the data would come from the customer-support system because it
stores old tickets and employee decisions. The website and mobile app
could provide the submission time, device type, app version, and the
customer’s selected category. Order and payment systems could provide
limited status information when it is related to the ticket.

### How much historical data might be useful?

ShopEase has about six months of old support tickets. I would start
with all usable tickets from those six months. The number of examples
also matters because each category needs enough examples for the model
to notice patterns. If one category has only a few tickets, the model
may not learn it well. The company should keep collecting new tickets
and update the model later.

### What would be the most important variables?

The ticket title and full message would be the most important because
they explain the customer’s problem. The category selected by the
customer could also help, even though it may not always be correct.
Other useful variables would be urgent words, app version, device type,
recent order status, past tickets, and the number of similar complaints
received recently.

### What could be missing or inaccurate?

Some customers may leave the title blank or write a message that is
too short to understand. A customer may select the wrong category, and
employees may have sorted similar tickets differently. Device or
app-version information may be missing. The system may also contain
duplicate tickets if a customer reported the same problem more than
once.


## Part 3 - Identify Features and Target

### 1. Features

Features are the information given to the model. I would use the
following features:

- Ticket title
- Full ticket message
- Category selected by the customer
- Date and time submitted
- Words or phrases that may show urgency
- Device type and operating system
- Website or mobile-app version
- Customer’s previous number of support tickets
- Recent order or payment status
- Number of similar tickets received recently

I would not include information just because it is available. For
example, a customer’s password or full card number is private and is
not needed to sort a ticket.

### 2. Target or output

The target is the answer that the model is supposed to learn. The main
target would be the correct support category:

- Account access
- Payment problem
- Order problem
- Technical error
- Feature request
- Other issue

The model would also give an urgent or not urgent label. If a ticket
is urgent, it would be moved to the front of the queue and sent to
senior support staff. An employee would check both labels before the
ticket is sent anywhere.


## Simple example

- Ticket: I was charged twice for the same order.
- Category: Payment problem
- Urgency: Urgent

- Ticket: The app closes whenever I open my cart.
- Category: Technical error
- Urgency: Not urgent


## Part 4 - Select the AI and ML Approach

### 1. Would I use supervised or unsupervised learning?

Supervised learning

### 2. Why did I choose it?

I chose supervised learning because ShopEase already has completed
tickets from the last six months. Employees have already given those
tickets a final category and decided which ones were urgent. These
known answers are the labels. The model could study the ticket
information, which contains the features, and compare it with the
labels. It could then use the patterns it learned to suggest labels
for a new ticket.

I would not use unsupervised learning as the main approach because
ShopEase already knows the categories it wants to use. Unsupervised
learning would make more sense if the company did not have known
categories and wanted the system to discover groups on its own.

### 3. Would the problem involve classification or prediction?

Classification

### 4. Why did I choose classification?

Classification is used when the output is a category. In this case,
the system would place a ticket into a group such as payment problem,
technical error, or account access. Urgent and not urgent are also
categories. The model is not trying to estimate a number such as
future sales, revenue, or product demand. For that reason,
classification fits this problem better than numerical prediction.


## How the model could be trained and tested

ShopEase would first clean the six months of ticket data. It could use
about 80 percent of the usable tickets as training data and keep
20 percent as testing data. The model would learn from the training
tickets. The testing tickets would be used afterward to see how well
the model works on examples it did not see during training. This would
help show whether it learned a useful pattern instead of memorizing the
old tickets.


## How the result could be checked

Accuracy would show how many tickets were classified correctly overall.
However, urgent tickets may be less common, so accuracy alone may not
explain everything. Recall would show how many of the real urgent
tickets the system found. Precision would show how often a ticket
marked urgent was actually urgent. I would pay close attention to
recall because missing an urgent ticket could cause a serious
customer-service problem.


## Part 5 - Data Quality and Business Impact

### 1. Three possible data-quality problems

- Missing information - A ticket may have no title, an unclear message,
  or missing device information.
- Incorrect or inconsistent information - Customers or employees may
  have selected the wrong category.
- Duplicate or outdated records - The same problem may appear several
  times, or an old ticket may refer to an app version that is no longer
  used.

### 2. What could happen if the data is poor?

Poor data could teach the model incorrect patterns. A payment problem
might be sent to technical support, or an urgent ticket might remain at
the end of the queue. Employees would then spend more time correcting
the system instead of saving time. Customers could receive slower
service and lose trust in ShopEase. Private customer information could
also be exposed if the ticket data is not protected properly.

Poor data -> Poor model -> Poor decision -> Poor customer experience


## Human review

I would not allow the AI system to make the final decision by itself.
An employee would check every category and urgency suggestion. If the
model made a mistake, the employee would correct it before routing the
ticket. These corrections could later be used as new training examples.
This would let AI reduce repetitive work while keeping people
responsible for the final decision.


## Part 6 - AI Solution Summary

### Business Problem

ShopEase spends too much time manually sorting customer-support
tickets, and urgent tickets may be delayed.

### Data Needed

Six months of ticket titles, messages, final categories, urgency
labels, submission times, device details, app versions, and relevant
order or payment information.

### AI and ML Approach

A classification model would learn patterns from completed support
tickets and suggest labels for new tickets.

### Type of Learning

Supervised learning, because the old tickets already have known
categories and urgency decisions.

### Model Output

A suggested support category and an urgent or not urgent label.

### Business Benefit

Faster replies, fewer tickets sent to the wrong team, less manual
sorting, and better use of a small support staff.

### Potential Risk

The system could select the wrong category, miss an urgent ticket,
treat customers unfairly, or expose private information.


## Final conclusion

I think AI could help with this problem because customer messages do
not always follow simple rules. A supervised classification model
could learn from ShopEase’s completed tickets and suggest where a new
ticket belongs. It could also identify tickets that may need urgent
attention. The employee would still make the final decision. This
would make the AI a support tool for the team instead of a replacement
for human judgment.
