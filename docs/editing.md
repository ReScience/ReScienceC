Editorial Guide
===============

ReScience C conducts all peer review and editorial processes in the open, on the GitHub issue tracker.

ReScience C editors manage the review workflow with the help of our bot, `@editorialbot`. The bot is summoned with commands typed directly on the GitHub review issues. For a list of commands, type: `@editorialbot commands`.

```eval_rst
.. note:: To learn more about ``@editorialbot``'s functionalities, take a look at our `dedicated guide <editorial_bot.html>`_.
```

## Pre-review

Once a submission comes in, it will be in the queue for a quick check by the Track Editor-in-chief (TEiC). From there, it moves to a `PRE-REVIEW` issue, where the TEiC will assign a handling editor, and the author can suggest reviewers. Initial direction to the authors for improving the paper can already happen here, especially if the paper lacks some requested sections.

```eval_rst
.. important:: If the paper is out-of-scope for ReScience C, editors assess this and notify the author in the ``PRE-REVIEW`` issue.
```

Editors can flag submissions of questionable scope using the command `@editorialbot query scope`.

The TEiC assigns an editor (or a volunteering editor self-assigns) with the command `@editorialbot assign @username as editor` in a comment.

```eval_rst
.. note:: Please check in on the `dashboard <https://resciencec.theoj.org/dashboard/incoming>`_ semi-regularly to see which papers are currently without an editor, and if possible, volunteer to edit papers that look to be in your domain. If you choose to be an editor in the issue thread type the command ``@editorialbot assign @yourhandle as editor`` or simply ``@editorialbot assign me as editor``
```

### How papers are assigned to editors

By default, unless an editor volunteers, the Track Editor-in-chief (TEiC) on duty will attempt to assign an incoming paper to the most suitable handling editor. While TEiC will make every effort to match a submission with the most appropriate editor, there are a number of situations where an TEiC may assign a paper to an editor that doesn't fit entirely within the editor's research domains:

- If there's no obvious fit to _any_ of the ReScience C editors
- If the most suitable editor is already handling a large number of papers
- If the chosen editor has a lighter editorial load than other editors

In most cases, the TEiC will ask one or more editors to edit a submission (e.g. `@editor1, @editor2 - would one of you be willing to edit this submission for ReScience C`). If the editor doesn't respond within ~3 working days, the TEiC may assign the paper to the editor regardless.

Editors may also be invited to edit over email when an TEiC runs the command `@editorialbot invite @editor1 as editor`.

### Finding reviewers

At this point, the handling editor's job is to identify reviewers who have sufficient expertise in the field of software and in the field of the submission. ReScience C papers have to have a minimum of two reviewers, except for reproduction reports that require only a single review. In some cases, the editor also might want to formally add themselves as one of the reviewers. If the editor feels particularly unsure of the submission, a third (or fourth) reviewer can be recruited.

To recruit reviewers, the handling editor can mention them in the `PRE-REVIEW` issue with their GitHub handle, ping them on social networks (Mastodon, BlueSky, Twitter), or email them. After expressing initial interest, candidate reviewers may need a longer explanation via email. See sample reviewer invitation email, below.

Selection and assignment of reviewers should adhere to the [ReScience C COI policy](https://resciencec.readthedocs.io/en/latest/reviewer_guidelines.html).

**Potential ways to find reviewers**

Finding reviewers can be challenging, especially if a submission is outside of your immediate area of expertise. Some strategies you can use to identify potential candidates:

- Search the [reviewer application](https://reviewers.resciencec.theoj.org) of volunteer reviewers.
  - When using this spreadsheet, pay attention to the number of reviews this individual is already doing to avoid overloading them.
  - It can be helpful to use the "Data > Filter Views" capability to temporarily filter the table view to include only people with language or domain expertise matching the paper.
- Ask the author(s): You are free to ask the submitting author to suggest possible reviewers by using the [reviewer application](https://reviewers.resciencec.theoj.org) and also people from their professional network. In this situation, the editor still needs to verify that their suggestions are appropriate.
- Use your professional network: You're welcome to invite people you know of who might be able to give a good review.
- Search Google and GitHub for related work, and write to the authors of that related work.
- Ask on social networks: Sometimes asking on Mastodon for reviewers can identify good candidates.
- Check the works being referenced in the submission. Their authors may be interested in reviewing the submission.
- Avoid asking ReScience C editors to review: If at all possible, avoid asking editors to review as they are generally very busy editing their own papers.

Once a reviewer accepts, the handling editor runs the command `@editorialbot add @username as reviewer` in the `PRE-REVIEW` issue. Add more reviewers with the same command.
Under the uncommon circumstance that a review must be started before all reviewers have been identified (e.g., if finding a second reviewer is taking a long time and the first reviewer wants to get started), an editor may elect to start the review and add the remaining reviewers later. To accomplish this, the editor will need to hand-edit the review checklist to create space for the reviewers added after the review issues is created.

### Starting the review

Next, run the command `@editorialbot start review`. If you haven't assigned an editor and reviewer, this command will fail and `@editorialbot` will tell you this. This will open the `REVIEW` issue, with prepared review checklists for each reviewer, and instructions. The editor should move the conversation to the separate `REVIEW` issue.

## Review

The `REVIEW` issue contains some instructions for the reviewers to get a checklist using the command `@editorialbot generate my checklist`. The reviewer(s) should check off items of the checklist one-by-one, until done. In the meantime, reviewers can engage the authors freely in a conversation aimed at improving the paper.

If a reviewer recants their commitment or is unresponsive, editors can remove them with the command `@editorialbot remove @username from reviewers`. You can also add new reviewers in the `REVIEW` issue.

Comments in the `REVIEW` issue should be kept brief, as much as possible, with more lengthy suggestions or requests posted as separate issues, directly in the submission repository. A link-back to those issues in the `REVIEW` is helpful.

When the reviewers are satisfied with the improvements, we ask that they confirm their recommendation to accept the submission.

### Adding a new reviewer once the review has started

Sometimes you'll need to add a new reviewer once the main review (i.e. post pre-review) is already underway. In this situation you should do the following:

- In the review thread, do `@editorialbot add @newreviewer as reviewer`.
- The new reviewer must use the command `@editorialbot generate my checklist` to get a checklist.


## After reviewers recommend acceptance

You can ask EditorialBot to generate a checklist with all the post-review steps running the command: `@editorialbot create post-review checklist`

Pre-publication steps:
- Get a new proof with the `@editorialbot generate pdf` command.
- Download the proof, check all references have DOIs, follow the links and check the references.
  - EditorialBot can help check references with the command `@editorialbot check references`
- Proof-read the paper and ask authors to fix any remaining typos, badly formed citations, awkward wording, etc..
- Ask the author to make a tagged release and archive, and report the version number and archive DOI in the review thread.
- Check the archive deposit has the correct metadata (title and author list), and request the author edit it if it doesn’t match the paper.
- Run `@editorialbot set <doi> as archive`.
- Run `@editorialbot recommend-accept` to generate the final proofs, which has EditorialBot notify the `@resciencec/editors` team that the paper is ready for final processing.

At this point, the EiC/AEiC will take over to make final checks and publish the paper.

It’s also a good idea to ask the authors to check the proof. We’ve had a few papers request a post-publication change of author list, for example—this requires a manual download/compile/deposit cycle and should be a rare event.

## Rejecting a paper

If you believe a submission should be rejected, for example, because it is out of scope for ReScience C, then you should:

- Ask EditorialBot to flag the submission as potentially out of scope with the command `@editorialbot query scope`. This command adds the `query-scope` label to the issue.
- Mention to the author your reasons for flagging the submission as possibly out of scope, and _optionally_ give them an opportunity to defend their submission.
- During the scope review process, the editorial team may ask the authors to provide additional information about their submission to assist the editorial board with their decision.
- The TEiC will make a final determination of whether a submission is in scope, taking into account the feedback of other editors.

**Scope reviews for resubmissions**

In the event that an author re-submits a paper to ReScience C that was previously rejected, the TEiC will use their discretion to determine: 1) whether a full scope review by the entire editorial team is necessary, 2) if the previous reasons for rejection remain valid, or 3) if there have been enough updates to warrant sending the submission out for review.

## Sample messages for authors and reviewers

### Sample email to potential reviewers

```
Dear Dr. Jekyll,

I found you following links from the page of The Super Project and/or on Twitter. This message is to ask if you can help us out with a submission to the ReScience C journal (https://resciencec.theoj.org), where I’m an editor.

ReScience C publishes articles that report on replication or reproduction efforts in computational science. The submission I'd like youto review is titled: "title of the submission here"

The submission repository is at: https://github.com/< … >

ReScience C is a platinum open-access peer-reviewed online journal.

The review process at ReScience C is special: it takes place in a GitHub issue, is open, and author-reviewer-editor conversations are encouraged. The goal of a review should be to help the authors to improve their submission.

ReScience C reviews involve downloading and installing software, and inspecting the repository and submitted paper. See https://resciencec.readthedocs.io/en/latest/reviewer_guidelines.html

Editors and reviewers post comments on the review issue, and authors respond to the comments and improve their submission until acceptance (or withdrawal, if they feel unable to satisfy the review).

Would you be able to review this submission for ReScience C? If not, can you recommend someone from your team to help out?

Kind regards,

ReScience C Editor.
```

### GitHub invite to potential reviewers

```
:wave: @reviewer1 & @reviewer2, would any of you be willing to review this submission for ReScience C? We carry out our reviews here in GitHub issues and follow these guidelines: https://resciencec.readthedocs.io/en/latest/reviewer_guidelines.html
```

## Overview of editorial process

**Step 1: An author submits a paper.**

The author can choose to select an preferred editor based on the information available in our biographies. This can be changed later.

**Step 2: If you are selected as an editor you get @-mentioned in the pre-review issue.**

This doesn’t mean that you’re the editor, just that you’ve been suggested by the author.

**Step 3: Once you are the editor, find the link to the code repository in the `pre-review` issue**

- If the paper is not in the default branch, add it to the issue with the command: `@editorialbot set branch-where-paper-is as branch`.

**Step 4: The editor looks at the submission and checks to see if:**

- There’s an article
- There is code for generating the results shown in the article.

**Step 5: The editor responds to the author saying that things look in line (or not) and will search for reviewer**

**Step 6: The editor finds >= 2 reviewers**

- Use the list of reviewers: type the command `@editorialbot list reviewers` or
  look at use the [Reviewers Management System](https://reviewers.resciencec.theoj.org)
- If people are in the review list, the editor can @-mention them on the issue to see if they will review: e.g. `@person1 @person2 can you review this submission for ReScience C?`
- Or solicit reviewers outside the list. Send an email to people describing what ReScience C is and asking if they would be interested in reviewing.
- If you ask the author to suggest potential reviewers, please be sure to tell the author not to @-tag their suggestions.

**Step 7: Editor tells EditorialBot to assign the reviewers to the paper**

- Use `@editorialbot add @reviewer as reviewer`
- To add a second reviewer use `@editorialbot add @reviewer2 as reviewer`

**Step 8: Create the actual review issue**

- Use `@editorialbot start review`
- An issue is created with the review checklist, one per reviewer, e.g. https://github.com/resciencec/resciencec-reviews/issues/1

**Step 9: Close the pre-review issue**

**Step 10: The actual review**

- The reviewer reviews the paper and has a conversation with the author. The editor lurks on this conversation and comes in if needed for questions (or CoC issues).
- The reviewer potentially asks for changes and the author makes changes. Everyone agrees it’s ready.

**Step 11: The editor pings the EiC team to get the paper published**

- Make a final check of the paper with `@editorialbot generate pdf` and that all references have DOIs (where appropriate) with `@editorialbot check references`.
- Editors can get a checklist of the final steps using the `@editorialbot create post-review checklist` command
- Finally, use `@editorialbot recommend-accept` on the review thread to ping the `@resciencec/editors` team letting them know the paper is ready to be accepted.

**Step 12: Celebrate publication! Thank reviewers! Say thank you on issue.**

## Tips for ReScience C editors

**Aim for reviewer redundancy**  

If you have 3 people agree to review, take them up on their offer(s), that way if one person drops out, you'll have a backup and won't have to look for more reviewers. Also, when sending invites, try pinging a number of people at the same time rather than doing it one-by-one.

**Email is a good backup**  

Email is often the most reliable way of contacting people. Whether it's inviting reviewers, following up with reviewers or authors etc., if you've not heard back from someone on GitHub, try emailing them (their email is often available on their GitHub profile page).

**Default to over-communicating**   

When you take an action (even if it isn't on GitHub), share on the review thready what you're up to. For example, if you're looking for reviewers and are sending emails – leave a note on the review thread saying as much. 

**Ask reviewers to complete their review in 4-6 weeks**

We aim for a total submission ... publication time of ~3 months. This means we ideally want reviewers to complete their review in 4-6 weeks (max).

**Use saved replies on GitHub**

[Saved replies](https://docs.github.com/en/get-started/writing-on-github/working-with-saved-replies/using-saved-replies) on GitHub can be a huge productivity boost. Try making some using the example messages listed above.

**Ping reviewers if they’ve not started after 2 weeks** 

If a reviewer hasn't started within 1-2 weeks, you should probably give them a nudge. People often agree to review, and then forget about the review.

**Learn how to nudge gently, and often**

One of your jobs as the editor is to ensure the review keeps moving at a reasonable pace. If nothing has happened for a week or so, consider nudging the author or reviewers (depending upon who you're waiting for). A friendly _"👋 reviewer, how are you getting along here"_ can often be sufficient to get things moving again. 

**Check in twice a week**

Try to check in on your ReScience C submissions twice per week, even if only for 5 minutes. Use your dashboard to stay on top of the current status of your submissions (i.e., who was the last person to comment on the thread).

**Leave feedback on reviewers**

Leave feedback on the [reviewers application](https://reviewers.resciencec.theoj.org/) at the end of the review. This helps future editors when they're seeking out good reviewer candidates.
