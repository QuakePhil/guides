# Ticket Creation Guidelines for Client Services

When opening a ticket, the first step is deciding if you are reporting a TASK or a BUG. Here is a good rule of thumb:
- If something is supposed to exist but doesn't, it is a TASK.
- If something is supposed to work but doesn't, it is a BUG.

---

Second, in order to add as much at-a-glance information to the ticket as possible there are 3 questions that should be
answered by the title:
- **WHO**?
- **WHAT**?
- **WHERE**?

These should be formatted in the following manner:
- TASK: "As a **WHO** I want to **WHAT** in **WHERE**"
- BUG: "BUG! As a **WHO** **WHAT** in **WHERE** **WHAT**"

Some standard values for **WHO** are PUBLISHER, LICENSEE, BUSINESS USER, and ENGINEER. Other values can be used, but these
should cover most use cases. Try to think of who is ultimately going to be affected by the issue at hand. You may be
working on it, but does it directly impact you, or perhaps someone else downstream?

Bugs tend to have two verb clauses, that's why there are two "**WHAT**"s in the BUG format,
i.e. "I did ____ in QA and it ______"

Here are some examples:

TASK

_Bad_: Automate Statement Data Load
_Better_: As an ENGINEER I want to automate statement data load
_Best_: As an ENGINEER I want to automate the loading of statement data from Siren to Oracle (STMPRD)

_Bad_: Use British Pounds for Voucher
_Better_: As an ENGINEER I want to generate vouchers with British Pounds
_Best_: As a PUBLISHER I want vouchers from MINT payments to use British Pounds

_Bad_: Make description of statement types
_Better_: As a CLIENT I want to download a description of what a statement is
_Best_: As a PUBLISHER I want to be able to download a description for each type of statement that is available to me

BUG

_Bad_: BUG: Eight Five Dollar and Two Thousand, One Hundred and Sixteen Cents payment
_Better_: BUG! As a BUSINESS USER payment vouchers are broken in QA
_Best_: BUG! As a PUBLISHER when I download a voucher in QA, the word amount on the check is incorrect

_Bad_: LR - Empty Regular User Reports
_Better_: BUG! As a USER reports are empty
_Best_: BUG! As a PUBLISHER when I download a License Report in QA, the report is empty.

_Bad_: BUG! Writer data is wrong
_Better_: BUG! Writer data possibly incorrect for compositions belonging to Carlin America INC (P47652)
_Best_: BUG! As a PUBLISHER when I view a composition in the roydash in QA, the writers for the composition are incorrect.

---

The next question to answer is "WHY?", and this should be addressed clearly and concisely in the description section of
the ticket along with any other details that may be helpful for those assigned to the ticket to understand the task or
recreate the bug. These details include:
- User
- Publisher
- Data Specific to the Issue (such as Check #)
- Environment (QA, demo/dev, prod?)
- Date/Time Stamp
- What happened
- Expected result if different from what happened

Here's an example:

_Bad_:

_Better_: Using fbrito@sesac on QA with check 1239783 the total amount is 87123.23 instead of 87123.24

_Best_:
User
fbrito@sesac.com

Environment
QA

Data
Check 1239783

What Happened
Total amount is 87123.23

What I expected to happen
The total to be 87123.24
