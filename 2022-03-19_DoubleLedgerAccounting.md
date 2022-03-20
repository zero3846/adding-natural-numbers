# Double Ledger Accounting

Date: 2022-03-19 11:12 PM CDT
Tags: accounting

As I was self-teaching myself about accounting, every explanation I came across kept barraging me with a ton of jargon. Hopefully, I can explain the double ledger system in a much more natural and organic way without all the business words.

Unlearn what you think "debit" and "credit" means. It just means left and right.

If you were learning accounting yourself, you may have heard of the accounting equation, where all your assets must equal all your liabilities plus your equities, but being too lazy to go into what all those mean, I offer this simplification:

- left = what you have
- right = what others give you
- debit = transfer into an account
- credit = transfer from an account

Note that while I said that debit is left and credit is right, they are overloaded terms in actual double ledger terminology, because they are nouns as well as verbs. I use left/right for nouns and debit/credit for the verbs.

Now, onto a specific scenario. Imagine, you get paid $100 direct deposited into your checking account. You plan on spending $50 in groceries. You actually spend $55. Plus, you also bought a $60 bike on your credit card for some reason. On a double ledger, this would read something like this.

+------------------+---------+----------+-------------+---------+----------+
| L Account        | L Debit | L Credit | R Account   | R Debit | R Credit |
+------------------+---------+----------+-------------+---------+----------+
|                  |         |          | Income      |         |     $100 |
| Checking         |    $100 |          |             |         |          |
| Checking         |         |      $50 |             |         |          |
| Groceries Budget |     $50 |          |             |         |          |
| Groceries Budget |         |      $55 |             |         |          |
| Groceries        |     $55 |          |             |         |          |
|                  |         |          | Credit Card |         |      $50 |
| Bike             |     $50 |          |             |         |          |
+------------------+---------+----------+-------------+---------+----------+
| L Total          |    $255 |     $105 | R Total     |      $0 |     $150 |
+------------------+---------+----------+-------------+---------+----------+

"L Total" = "L Debit" - "L Credit" = $150
"R Total" = "R Credit" - "R Debit" = $150

There are a few things to notice. I'll start with the fact that Income and Credit Card are on the right side. This is because this is money that is given to you. This helps you keep track of what you may owe. Not everything on the right is what you owe, but it did come from someone else.

Next is that both the left and right totals are equal. This isn't by accident. Every new credit is matched with a subsequent debit and vice versa.

The L Total and R Total equations look like they flip their respective debit and credit terms. This makes sense because the left total, representing what you are **left** with, is simply what was transferred into your possession (debit) minus what was transferred out of your possession (credit). Similarly, the right total, representing the net total others gave you, is the total of transfers from them (credit) minus the total transfers to them (debit).

Now if we were to inspect the total debits and credits for each account, we'll notice that one of the totals is negative. We'll show this in a single ledger format for convenience.

+------------------+---------+----------+---------+---------+
| Account          | Debit   | Credit   | L Total | R Total |
+------------------+---------+----------+---------+---------+
| Income           |      $0 |     $100 |         |    $100 |
| Checking         |    $100 |      $50 |     $50 |         |
| Groceries Budget |     $50 |      $55 |     -$5 |         |
| Groceries        |     $55 |       $0 |     $55 |         |
| Credit Card      |      $0 |      $50 |         |     $50 |
| Bike             |     $50 |       $0 |     $50 |         |
+------------------+---------+----------+---------+---------+

In general, we don't like negative numbers in these ledgers, but there ways to fix that. In this case, we just allocate an additional $5 from Checking to Groceries Budget. It's worth noting that this was obvious in the beginning, but when there are lots of transactions involved, it helps to know you can find these things programmatically.

+------------------+---------+----------+-------------+---------+----------+
| L Account        | L Debit | L Credit | R Account   | R Debit | R Credit |
+------------------+---------+----------+-------------+---------+----------+
| Checking         |         |       $5 |             |         |          |
| Groceries Budget |      $5 |          |             |         |          |
+------------------+---------+----------+-------------+---------+----------+

+------------------+---------+----------+---------+---------+
| Account          | Debit   | Credit   | L Total | R Total |
+------------------+---------+----------+---------+---------+
| Checking         |    $100 |      $55 |     $45 |         |
| Groceries Budget |     $55 |      $55 |      $0 |         |
| Credit Card      |      $0 |      $50 |         |     $50 |
+------------------+---------+----------+---------+---------+

Now that we've resolved that issue, we realize that now we need to pay back that Credit Card. This isn't a fact that can be known from the ledger alone, but it's something that we know about how credit cards work. Here's where we run into a problem. We are short $5. How would this get expressed in the double ledger? We can just create another account. We'll call it Shortfall.

+------------------+---------+----------+-------------+---------+----------+
| L Account        | L Debit | L Credit | R Account   | R Debit | R Credit |
+------------------+---------+----------+-------------+---------+----------+
|                  |         |          | Shortfall   |         |       $5 |
| Checking         |      $5 |          |             |         |          |
| Checking         |         |      $50 |             |         |          |
|                  |         |          | Credit Card |     $50 |          |
+------------------+---------+----------+-------------+---------+----------+

+------------------+---------+----------+---------+---------+
| Account          | Debit   | Credit   | L Total | R Total |
+------------------+---------+----------+---------+---------+
| Checking         |    $105 |     $105 |      $0 |         |
| Credit Card      |     $50 |      $50 |         |      $0 |
| Shortfall        |      $0 |       $5 |         |      $5 |
+------------------+---------+----------+---------+---------+

Again, using knowledge outside of the ledger, we know that Shortfall tells us we need money from somewhere else, but now that we have it, we can resolve how we'll pay for the Credit Card. Now you just need $5. Lucky for you, you found a $5 bill, and you can deposit it into  your checking account.

+------------------+---------+----------+-------------+---------+----------+
| L Account        | L Debit | L Credit | R Account   | R Debit | R Credit |
+------------------+---------+----------+-------------+---------+----------+
|                  |         |          | Cash Found  |         |       $5 |
|                  |         |          | Shortfall   |      $5 |          |
+------------------+---------+----------+-------------+---------+----------+

+------------------+---------+----------+---------+---------+
| Account          | Debit   | Credit   | L Total | R Total |
+------------------+---------+----------+---------+---------+
| Cash Found       |      $0 |       $5 |         |      $5 |
| Shortfall        |      $5 |       $5 |         |      $0 |
+------------------+---------+----------+---------+---------+

Now, there's really nothing wrong with the ledger, and you can finally close this chapter of your life.
