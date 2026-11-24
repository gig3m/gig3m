# A hiring site for a business that mostly hires by word of mouth

**The business:** the same manufacturer. Most of our hiring (yard and production labor, truck drivers) is never posted anywhere.

## The problem

Applications came in however people could get them to us. Driver applicants need a longer federal (DOT) application. Nobody could quickly answer "who applied for the driver job last month, and where are they in the process?"

## What I built

A small hiring site, also built with coding agents under a written review checklist:

- **Applicants sign in with their email.** There are no passwords to forget. They can apply in general or for specific open roles, and drivers get the DOT application instead of the standard one.
- **Sensitive data is protected.** Answers and ID uploads are encrypted at rest, and documents are only served to staff, with every view logged. The review checklist for every change starts with "what would expose an applicant's data."
- **Staff get an admin** with applicant status, notes, and requests for more forms.
- **An AI assistant can help.** Staff can ask Claude to find applicants, summarize where someone stands, or draft and post a job opening. Social Security and license numbers come back masked, the assistant can't change applicants, and opening a role takes a preview and a person's OK.
- **Rules are built in.** Openings never list pay, since it depends on experience, and the application follows the Texas rule against asking about criminal history.

## What changed

Every application lands in one place, sensitive details stay encrypted and logged, and staff can post an opening by asking the assistant.
