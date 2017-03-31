## Inventory Directory

This directory lists what the main sleuths, Courtney and Jezebel, have in their possession. This directory is expressly for the user to alter in the course of the tale. You can alter them however you see fit.  As things progress, you will find changes in story direction (i.e. commits for checkout) based on modifications you've made to these files.  Having additional weapons, or carrying compromising materials, may present you with new story choices. 

You are on the honor system to checkout out the commits that are appropriate to your inventory. You could theoretically put anything you want in these files. Note, however, the author has only written story variations (commits) based on what's listed as available in the texts. It's unlikely that Jezebel or Courtney will ever have access to a tank, thus unlikely the original author has any story variation based upon that. But feel free to fork the repo and include a dramatic tank battle if you want to (that's part of the fun.)

Note that the creator of Gang of Gits has crafted the repository in such a way that mistakes made in using git should be relatively easy to recover from. If for any reason you are so confused that you want to start over, just clone the repo to start from scratch, and checkout the commit you were on before the mess started.

### Clothes.md 

This file notes what the main characters, Courtney / Jezebel are wearing.
It should come in use in the following scenarios:

- Change of Neighborhoods. Characters may be faced with quick decisions that may cause their appearance to make them out of place. Gang colors, or appearing too high / low class may pose serious problems. This shouldn't occur too often, but if the reader _never_ chooses to stop and think, the sleuths never take the time to switch clothing. 

### Weather.md

A list of relevant weather conditions. Time of day, sunlight / moonlight, etc. affect visibility. Rain, snow, and ice may effect road conditions. Author warns weather conditions may lead of adverse outcomes in some of the following examples. 

- Tracking suspects, especially if binoculars are necessary.
- Risky car maneuvers during chases
- Attempting to transport large amounts of paper in the rain.
- Anything involving gunfire, especially sniping.

### Weapons.md

This file keeps track of what Courtney and Jezebel have to protect themselves in case of altercation. Unless stated otherwise Jezebel keeps a .22 pistol with silencer in an improvised hoster that sticks to the small of her back, and Courtney keeps pepper spray in her pocket. If a more proficient git user wishes to arm the pair better, this may be done by manually altering this file and keeping track of it. It is of course up to the user to only check out bonus endings that may arise from change of firepower. 

### How to track changes to this directory

**Note**: this info isn't a replacement for a more traditional git tutorial that explains in detail what git does and how it works. This info is to allow you to *practice* the commands a tutorial will teach you with a live repo in which you have a goal. 

Git keeps information stored in commits, which contain a collection of different kinds of data (i.e. they are what programmers call objects). They record the state of your project's files at a given point in time. They are essentially snapshots. If your project reachs a state you think you may want to go back to, you commit it. If you ever want to go back to that state, you merely check it out. Much like a book from a library, your files will all be there as recorded. 

As git is a record of changes over time, every time you commit, the new commit is considered to be the child of the old commit, which is its parent. As programmers often experiment with multiple implementations, git implements the concept of branches, which let your project changes diverge over time. Implementations begin to be settled on, and keeping two or more diverging series of commits (i.e. two branches) is no longer desirable. The desired changes are merged into a new commit, a merge commit. 

Merging can get tricky if diverging series of commits (branches) you're trying to merge have altered the same file. Git is good at managing changes to different files, but when the same file is changed in two different ways, git can't figure out what changes to keep. You have to manually edit the file so that your new merge commit has the file exactly the way you want it. Once the merge is complete, you may have no further need for the branch, and can delete it. 

Let's say you want to change the weapons.md file for more firepower. As you're diverging from the main story line, let's make a separate branch: **git branch weapons** then check it out **git checkout weapons**. Add the changes to weapons.md to list of changes you want to record in the next commit: **git add weapons.md**. You can check the status of what's changed and what files are going into your commit with **git status**. Then **git commit**. Write a message describing how you changed the weapons.md file. (See, [what makes a good commit message](#) for help). Then checkout the previous branch **git checkout <previous commit>** where previous commit is the commit you wish to return to. 

In this state, you will always be able to recover your weapons.md file with the following: **git checkout weapons -- weapons.md**. The -- in the command tells git to handle the remaining parts of commands as file names. Here, you are telling git to return weapons.md to the state it was in when you last committed it to the weapons branch. You can continue the story as it's being told. However, you're likely to have some problems the next time you checkout a new branch. Git will note you have some uncommitted changes that will be destroyed if you checkout a new branch and do nothing. You can force it to proceed with **git checkout -f <destination commit>** where destination is the branch you'd like to checkout. Then **git checkout weapons -- weapons.md** will get your weapons back.

Git also has a concept of stashing changes, which allows you to checkout without losing your work. If git stops you from checking out due to unsaved changes you can type **git stash save**, **git checkout <destination commit>**, then **git stash apply**. Stashing is intended to be a temporary save, not a managing system, and will work best in the number of changes is small. 

### To start really using git

Since this adventure is just as much about using git as it is the adventure itself, I also suggest this more messy strategy. Create a branch called inventory: **git branch inventory**. Add any changes with **git add <file>** and commit them. This is how you will keep track of changes to your inventory. In order to progress the story along, rather than checking out the commit, merge it instead: **git merge <destination commit>**. With checkout you go to a record of the project in a previous state. With a merge, you're taking in all the changes of that state and applying them to the commit that's currently checked out. You can then add all those files (individually or with **git add -A**) and commit them. 

If you change the same file when trying to merge two commits, git won't be able to resolve that conflict on its own. If you change the files noted (weapons.md, weather.md, or clothes.md) which are subject to author change from scene to scene, you'll have to merge files manually. You'll have to find a tool that handles merges (I use vimdiff). The merges should be easy, because you'll generally only have to choose one file over the other. Still, managing merges isn't easy and can be super-intimidating for a beginner. Check your affected files to see if you've done things properly. In the context of this story's repo, a fix to a merge that went awry is to simply edit the markdown files back to the way you want them, and then do another commit. Continue merging the new commits as the story presents them, rather than checking them out. 

If you can get this process down, you're doing exactly what programmers do with merging and branching. 
