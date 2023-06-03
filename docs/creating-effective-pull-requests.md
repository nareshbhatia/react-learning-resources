# Creating Effective Pull Requests

> This is a Cliff Notes version of the popular article
> [How to Make Your Code Reviewer Fall in Love with You](https://mtlynch.io/code-review-love/)
> by Michael Lynch. Note that the original article uses the term _Change List_,
> which we have replaced with _Pull Request_ because that's the terminology used
> by GitHub.

When people talk about code reviews, they focus on the reviewer. There’s
scarcely any guidance on preparing your code for review. This article describes
best practices for participating in a code review when you’re the author.

## Why improve your code reviews?

Improving code review technique helps your reviewer, your team, and, most
importantly: you.

- **Learn faster**: If you prepare your PR properly, it directs your reviewer’s
  attention to areas that support your growth rather than boring style
  violations. When you demonstrate an appreciation for constructive criticism,
  your reviewer provides better feedback.

- **Make others better**: Your code review techniques set an example for your
  colleagues. Effective author practices rub off on your teammates, which makes
  your job easier when they send code to you.

- **Minimize team conflicts**: Code reviews are a common source of friction.
  Approaching them deliberately and conscientiously minimizes arguments.

## The golden rule: value your reviewer’s time

This advice sounds obvious, but I often see authors treat their reviewers like
personal quality assurance technicians. These authors make zero effort to catch
their own errors or to design their PR for reviewability.

Your teammate arrives at work each day with a finite supply of focus. If they
allocate some of it to you, that’s time they can’t spend on their own work. It’s
only fair that you maximize the value of their time.

Reviews drastically improve when both participants trust each other. Your
reviewer puts in more effort when they can count on you to take their feedback
seriously. Viewing your reviewer as an obstacle you have to overcome limits the
value they offer you.

## Techniques

### 1. Review your own code first

Before sending code to your teammate, read it yourself. Don’t just check for
mistakes — imagine reading the code for the first time. What might confuse you?

### 2. Write a clear PR description

Your PR description should summarize any background knowledge the reader needs.
You might have a code reviewer in mind when you write the description, but they
don’t necessarily have the context you imagine. Readers in the future should
understand your intentions when they look back on the change history.

A good PR description explains **what** the PR achieves, at a high level, and
**why** you’re making this change.

### 3. Automate the easy stuff

If you rely on your reviewer to tell you when your curly braces are on the wrong
line or that your change broke the automated test suite, you’re wasting their
time. Add git pre-commit hooks, linters, formatters, and tests to your
development environment to ensure that your code observes proper conventions and
preserves intended behavior on each commit.

### 4. Answer questions with the code itself

When your reviewer expresses confusion about how the code works, the solution
isn’t to explain it to that one person. You need to explain it to everyone.

The best way to answer someone’s question is to refactor the code and eliminate
the confusion. Can you rename things or restructure logic to make it more clear?
Code comments are an acceptable solution, but they’re strictly inferior to code
that documents itself naturally.

### 5. Narrowly scope changes

Scope creep is a common anti-pattern in code reviews. A developer starts to fix
a logic bug, but they notice a UI blemish in the process. “While I’m here,” they
think, “I’ll just fix this other thing.” But now they’ve muddled things. Their
reviewer has to figure out which changes serve goal A and which serve goal B.

The best PRs just
[Do One Thing](https://blog.codinghorror.com/curlys-law-do-one-thing/). The
smaller and simpler the change, the easier it is for the reviewer to keep all
the context in their head. Decoupling unrelated changes also allows you to
parallelize your reviews across teammates, reducing turnaround time for your
changes.

### 6. Separate functional and non-functional changes

Developers often mix functional and non-functional changes in their PRs. They’ll
make a two-line change, and then their code editor automatically reformats the
entire file. Now the PR ends up having a two-line functional change buried in
hundreds of lines of non-functional whitespace changes. This kind of PR is a
massive insult to your reviewer. If the formatting change is desired, make it a
separate PR.

### 7. Break up large PRs

A PR’s complexity grows exponentially with the number of code lines it touches.
When adding a large feature, can you change the dependencies first and add the
new feature in a subsequent PR?

It’s tedious to break up your code to find a subset that makes a working,
intelligible change, but it yields better feedback and puts less strain on your
reviewer.

### 8. Respond graciously to critiques

The fastest way to ruin a code review is to take feedback personally. This is
challenging, as many developers take pride in their work and see it as an
extension of themselves.

As the author, you ultimately control your reaction to feedback. Treat your
reviewer’s comments as an objective discussion about the code, not your personal
worth as a human. Responding defensively will only make things worse.

When a reviewer catches an embarrassing bug, praise them for their attention to
detail. When they catch a subtle flaw, it only indicates that you packaged your
PR well. Without obvious issues like bad formatting and confusing names, they
were able to focus deeply on logic and design, yielding more valuable feedback.

### 9. Be patient when your reviewer is wrong

From time to time, reviewers are flat out wrong. Just as you can accidentally
write buggy code, your reviewer can misunderstand correct code.

Even when your reviewer is mistaken, that’s still a red flag. If they misread
it, will others make the same mistake? Does the reader have to exercise an
abnormal level of scrutiny to reassure themselves that a particular bug _isn’t_
there?

Look for ways to refactor the code, or add comments that make the code more
obviously correct. If the confusion stems from obscure language features,
rewrite your code using mechanisms that are intelligible to non-experts.

### 10. Communicate your responses explicitly

We often run into a scenario where the reviewer gives someone comments, authors
update their code to address some of the feedback, but they don’t write any
replies. Now, we’re in an ambiguous state. Did they miss the other comments, or
are they still working?

Establish conventions on your team that make it clear who’s “holding the baton”
at any point. Either the author is working on edits, or the reviewer is writing
feedback. There should never be a situation where the process stalls because
nobody knows who’s doing what. You can accomplish this easily with PR-level
comments that indicate when you’re handing control back and forth. For example,
"Updated! Please take a look".

For every comment that requires action, respond explicitly to confirm that
you’ve addressed it. PRs on GitHub allow you to mark comments as resolved.
Otherwise, follow a simple convention, like, “Done,” for each comment. If you
disagree with the comment, politely explain why you declined to take action.

### 11. Artfully solicit missing information

Sometimes code review comments leave too much room for interpretation. When you
receive a comment like, “This function is confusing,” you probably wonder what
“confusing” means, exactly. Your instinct might be to ask, “What’s confusing
about it?” but that comes across as grouchy. Instead, try this:

> What changes would be helpful?

This response signals a lack of defensiveness and openness to criticism.

### 12. Award all ties to your reviewer

In tennis, when you’re unsure if your opponent’s serve landed out of bounds, you
give them the benefit of the doubt. There should be a similar expectation for
code reviews.

When your reviewer makes a suggestion, and you each have roughly equal evidence
to support your position, defer to your reviewer. Between the two of you, they
have a better perspective on what it’s like to read this code fresh.

### 13. Minimize lag between rounds of review

Often an author sends out a PR for review, receives feedback, then puts it on
the back burner for a week because another task distracted them. This lag
between rounds of review increases the reviewer's workload. Not only do they
have to re-read the code, but may also have to re-read their feedback to restore
the memory of the discussion.

Once you send a PR out, driving it to completion should be your highest
priority. Delays on your end waste time for the reviewer and increase merge
complexity for your whole team.

### Conclusion

As you prepare your next PR, consider the factors you control, and use them to
guide the review productively.

Remember the golden rule: value your reviewer’s time. A reviewer generates
high-quality feedback when you allow them to focus on the interesting parts of
your code. If you require them to untangle your code or police simple mistakes,
you both suffer.

Lastly, communicate thoughtfully. It’s frighteningly easy for simple
miscommunications or thoughtless comments to derail a review. So be conscious of
pitfalls that could make your reviewer feel attacked or disrespected.
