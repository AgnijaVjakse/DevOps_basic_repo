# DevOps repozitorijs
Agnija Vjakse DevOps repozitorijs pamati iesācējiem

Izmaiņas, kādas tika veiktas iepriekšējās nedēļas laikā:

Pirmais variants: git log --after=2022-04-25

agnija@agnija-VirtualBox:~/Desktop/git_repos/terraform$ git log --after=2022-04-25
commit 488853be9cc549527db3760573be459b2d49a74e (HEAD -> main, origin/main, origin/HEAD)
Author: Kevin Wang <kwangsan@gmail.com>
Date:   Fri Apr 29 15:33:45 2022 -0400

    fix: `img/docs/concrete-plan.png` (#30967)

commit 78f90a64b5d4f615efdcbdb92d88291012aba7c4
Merge: f19848bab 2928967b4
Author: Laura Pacilio <83350965+laurapacilio@users.noreply.github.com>
Date:   Fri Apr 29 11:58:17 2022 -0400

    Merge pull request #30956 from tigerblue77/patch-1
    
    Update apt.mdx

commit f19848babf83223216a30c21e206645daf0e7807
Merge: 0bcd04a56 8699b115a
Author: James Bardin <j.bardin@gmail.com>
Date:   Thu Apr 28 16:44:23 2022 -0400

    Merge pull request #30962 from hashicorp/jbardin/update-ssh
    
    udpate x/crypto/ssh

commit 8699b115a71390464807812249e04cbed336dbfa
Author: James Bardin <j.bardin@gmail.com>
Date:   Thu Apr 28 14:51:20 2022 -0400


Otrais variants: git log --since=1.weeks

agnija@agnija-VirtualBox:~/Desktop/git_repos/terraform$ git log --since=1.weeks
commit 488853be9cc549527db3760573be459b2d49a74e (HEAD -> main, origin/main, origin/HEAD)
Author: Kevin Wang <kwangsan@gmail.com>
Date:   Fri Apr 29 15:33:45 2022 -0400

    fix: `img/docs/concrete-plan.png` (#30967)

commit 78f90a64b5d4f615efdcbdb92d88291012aba7c4
Merge: f19848bab 2928967b4
Author: Laura Pacilio <83350965+laurapacilio@users.noreply.github.com>
Date:   Fri Apr 29 11:58:17 2022 -0400

    Merge pull request #30956 from tigerblue77/patch-1
    
    Update apt.mdx

commit f19848babf83223216a30c21e206645daf0e7807
Merge: 0bcd04a56 8699b115a
Author: James Bardin <j.bardin@gmail.com>
Date:   Thu Apr 28 16:44:23 2022 -0400

    Merge pull request #30962 from hashicorp/jbardin/update-ssh
    
    udpate x/crypto/ssh

commit 8699b115a71390464807812249e04cbed336dbfa
Author: James Bardin <j.bardin@gmail.com>
Date:   Thu Apr 28 14:51:20 2022 -0400



Atrast commit, kuru veica Laura Paccillo:

git log --since=1.weeks --author Laura
commit 78f90a64b5d4f615efdcbdb92d88291012aba7c4
Merge: f19848bab 2928967b4
Author: Laura Pacilio <83350965+laurapacilio@users.noreply.github.com>
Date:   Fri Apr 29 11:58:17 2022 -0400

    Merge pull request #30956 from tigerblue77/patch-1
    
    Update apt.mdx
    
    
    
Laura nav veikusi commit 2021.septembri

Laura nav veikusi commit vakar (2022-04-24)
 
Atlasot rezult'atus no 20.-21. aprilim, uzradaas 16. aprilja commit:
https://community.atlassian.com/t5/Bitbucket-questions/git-log-with-date-range-or-before-after/qaq-p/603965
Here's one idea:

- Rebase before you merge.   The rebase will leave all the "authorDate" meta-data alone on the rebased commits, but it will update the "commitDate" meta-data, which is what "git log --after" actually uses internally, even though it uses "authorDate" in its output (a git ux mistake IMO, quite confusing for users!).  And so if you rebase today, all commits that get rebased will be captured by a "git log --after yesterday" even though the dates they show look older.

More info here about what data "git log --after" is actually using (stackoverflow.com):  How to get git to show commits in a specified date range for author date?

 

Here's another idea:

- The merge commit itself should show up (its "commitDate" will be in July), just not the commits brought over by the merge.   Can you use the merge commit to calculate your metrics?

- Try "git log --first-parent -m -p" to get merge diffs into your git log output.   Normally "git log -p" does not include merges in the diff output.  You need to add "-m" to get their diffs to print.
    
    
    
    


