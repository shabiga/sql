# Assignment 1: Design a Logical Model

## Question 1
Create a logical model for a small bookstore. 📚

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).

## Question 2
We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.
CREATE TABLE Employee_Shift (
    Employee_shift_id INT PRIMARY KEY,
    Employee_id INT,
    Shift_date DATE,
    Shift_type_morning VARCHAR(10), 
    Shift_type_evening VARCHAR(10),
    FOREIGN KEY (Employee_id) REFERENCES Employee(Employee_id));



## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Bonus: Are there privacy implications to this, why or why not?
```
Your answer...
```
Type 1 architecture would be to Overwrite
CREATE TABLE CUSTOMER_ADDRESS_Type1 (
    Customer_id INT PRIMARY KEY,
    Address VARCHAR(255),
    City VARCHAR(100),
    State VARCHAR(100),
    Zip_Code VARCHAR(20));

Type 2 architecture would be to Retain changes 
CREATE TABLE CUSTOMER_ADDRESS_Type2 (
    Address_id INT PRIMARY KEY,
    Customer_id INT,
    Address VARCHAR(255),
    City VARCHAR(100),
    State VARCHAR(100),
    Zip_Code VARCHAR(20),
    Effective_date DATE,
    End_date DATE);

Both Type 1 and Type 2 architectures have privacy problems. There is a chance of inadvertent disclosure of personal information in type 1 if the overwritten address contains any sensitive data. For instance, if the customer moved and the address now belongs to a different person. Type 2 offers a higher risk of unauthorized access to private data, including former addresses and living arrangements, which could be misused. 

## Question 4
Review the AdventureWorks Schema [here](https://i.stack.imgur.com/LMu4W.gif)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
Your answer...
```
My ERD for the small bookstore and AdventureWorks Schema ERD differs in two ways: scope and complexity, and the number of tables and schemas. Beyond simple sales operations, a wide range of functionalities and business processes are covered by the AdventureWorks schema. It has relationships and tables for purchasing, sales, people, production, and human resources. My ERD, in contrast, seems to have a more focused approach, with a simpler structure that is more suited to the needs of a small bookstore. It appears to be specifically focused on sales-related entities, such as customers, orders, employees, dates, and books.
# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `June 1, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-3-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
