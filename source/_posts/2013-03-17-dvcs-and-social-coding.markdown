---
layout: post
title: "DVCS and social coding"
date: 2013-03-09 12:59
comments: true
categories: 
---

This blog entry should be considered as a supplement to Sebastien Auvray’s [Distributed Version Control Systems: A Not-So-Quick Guide Through](http://www.infoq.com/articles/dvcs-guide). The author concentrates on the technical parameters of the distributed version control systems (DVCS), while this is fine for someone looking to make a decision which implementation to choose, he is missing a major aspect of DVCS- the sociability. I will briefly discuss some sample workflows and discuss how the introduction of DVCS helped Open Source projects, by lowering the entry barrier and making collaboration easier. Some even based their whole business model around socialising coding, like Github

## Centralised vs distributed workflows
Traditional centralized source control tools suggest hierarchy. Developers work with a single repository containing all of the code, so they organize themselves into trees. In DVCS, branching and merging is made cheap. Developers work with trees and teams can (self-) organize into any graph they want (example given in the dictator and lieutenants workflow).
To prove my point I will be using git examples, as this is the DVCS I am most familiar with. As for the competitors presented in the original blogpost most of the DVCS implementations (bazaar, mercurial and others) are roughly equal in their functionality, but git leads in the number of users. Lets go through several workflows.

**Basic**- this is the most basic workflow. It is suitable for small projects, like university group coursework. There is a central(blessed) repository and each of the contributors have their local copy of it. While in their local repository, each of the developers can branch off, commit and merge even without network connection, which is impossible with CVS. When they are done working on their feature they push back to the main repository. There is the detail that before consequent pushes to the repository each of the developers must rebase his/her changes on top of the ones from the previous one. This is easily done in git with the **merge** or **rebase** command.

![central](http://i.imgur.com/sMpXsle.png?1)

**Integration manager**- This is another scenario, which is often implemented by open source projects, which have appointed main contributor, who is responsible to review the changes submitted by others, before pushing them to the main repo.

![manager](http://i.imgur.com/0HRyc0i.png?1)

**Dictator and lieutenants**- This is just the integration manager workflow with another level of control of the quality. The collaboration between the junior developer in the case below is not obligatory, but just show how much DVCS encourage user communication.

![dictator](http://i.imgur.com/LoFEVRU.png?1)

## What centralised VCS manages with process, distributed VCS let you manage with software.
### Peer Review With SVN

* I pull from master and make my edits. 
* When I'm done I send patches to my collaborators who read them and argue with me.
* If they want to work with my changes:
 * they pull another copy of master
 * apply my patches
 * generate patches of their own 
 * send me these patches

### Peer Review With git

* I branch off master and make my changes.
* I push my branch to a public location and email my collaborators to tell them where.
* My collaborators use my URI to make diffs on-the-fly against any branch they like, check out my branch, or make commits back to it.
* They still argue with me sometimes of course, but as often they just implement their suggestions in my branch.

## DVCS and open source projects
With the introduction of DVCS and their workflows for development, the barrier to contribution to Open Source Software (OSS) was reduced. Huge projects like Mozilla, Python, KDE, NetBeans, Eclipse, Gnome[1] have moved to DVCS. 

Some of the main complaints connected with the centralised systems were[1]:
* “basic tasks such as reverting changes to a previously saved state, creating branches, publishing one's changes with full revision history, etc.” Also, they mentioned that  “there was no place to contain intermediate work”
* that the change will significantly lower the barriers for external contributors and make it easier for their own developers to merge and accept changes that have been created by others and received sufficient community testing

As a result of OSS projects migrating to DVCS the entry barrier was lowered and the number of active and new contributors increased. There is no more the need for core developers to act as gatekeepers for all the code that is submitted to the project. Contribution ownership remains for the actual contributors and debugging applications became easier, since one can see who introduced a certain commit, possibly introducing a bug.
It wasn’t godsend only for the open source projects, some major commercial organizations with giant code bases use it extensively- Facebook, Staples, Verizon, Microsoft and many others. Git is so essential for Google, that they pay the main contributor Junio Hamano and the second-in-command to work on Git full-time.

## The social coding and Github
Even though contributing technically became easier with the rise of DVCS, the real blessing for the development of Open source came with the websites that socialised coding. A lot of companies tried and succeeded to a certain level, but I believe the gold standard for now is Github.
You know how you open your Facebook every once in a while to check if anything changed. Every time you notice something new that gives you that little hit of dopamine. That is what Github managed to accomplish, but with code, which makes it actually useful. Github is code-sharing service based on git. As well as repository hosting, they provide developers with graphical interface, bug tracking tools, communication forums and Wiki pages. The most noticeable function is the “forking”, which copies a repository from one user’s account to another. This makes contributing to open sources a breeze. Basicly, you can make changes to a code you have read-only permission and later if you want, you can choose to contribute the additional functionality back to the project, by using a pull request, which will merge your changes to the project tree.

## All in all
One of the major aspect in which DVCS changed the developer game is the social aspect. Moving from the hard-coded one-way hierarchical structure of centralised VCS to the distribution of power among a diaspora of developers brought by DVCS. Systems like git, mercurial and bazaar revolutionised the open source development, by lowering the barrier to entry and democratising open source development. Social coding became the slogan of some of one of the most emblematic developer websites - Github, which brought together the addictiveness of the social networks to something useful- coding





***References***

[1] Rodriguez-Bustos, C.; Aponte, J.; , "How Distributed Version Control Systems impact open source software projects," Mining Software Repositories (MSR), 2012 9th IEEE Working Conference on , vol., no., pp.36-39, 2-3 June 2012

[Wired: Lord of the Files: How GitHub Tamed Free Software (And More)](http://www.wired.com/wiredenterprise/2012/02/github/all/)

[TechRepublic: Don't fear the fork: How DVCS aids open source development](http://www.techrepublic.com/blog/opensource/dont-fear-the-fork-how-dvcs-aids-open-source-development/2199)