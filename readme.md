# QA

## Quick recap
The current version of the website is done with [webflow](https://webflow.com/) and the person who did the work:
* cannot give us access to the project
* cannot implement the QA himself
* can only import the QA as an `iframe` hosted somewhere else.

Here's a link to the webflow website: https://dynesis.webflow.io/

## The solution we went for
In order to have a quick QA box hosted somewhere that could be iframed into the webflow site, we decided to create a minimal static html + css + js page, have the repo in *Dynesis*'s gitlab and publish it via [GitLab pages](https://docs.gitlab.com/ee/user/project/pages/).

## How the static QA works
If you look at `index.html` you will see a bunch of `<section>` tags: only the first one is visible, while the others have `display` set to `none`.
Each of these `<section>` is a step in the QA; `js/qa.js` set the right thing visible at the right time, checking the `id` of each element and listening to user actions.

As the user progresses through the QA, js keeps track of their choices and answers; finally all these infos are wrapped in `json` and shipped to an email address through [formspree](https://formspree.io/) (temp solution to have the thing working while staying in a static page).

Currently the script needs the following to work:
* element ids
* the `btn-question1` `btn-question2` `btn-question3` classes

All other classes used for giving the thing an initial raw styling. (Most of is is [w3.css](https://github.com/vitorlans/w3-css) based).

## What needs to be done
**Premise: I'm not a web person. I drafted the thing in a quick and dirty fashion with the goal of having a working draft that somebody would eventually polish.**
With this in mind here's a list of needed action:

1. **Make it pretty**. Things are currently more or less the right size, position and color, but that's it: it needs proper styling. Feel free to throw away the `w3.css` draft I did.

2. **If you have a better idea than formspree, go for it**. I don't like this email solution; just went to the low hanging fruit.

3. **The current js is quick and dirty: feel free to improve, if you feel inspired**. It does the job, but it could benefit from a frontender pass. Again: if you feel inspired: it's all yours :)
