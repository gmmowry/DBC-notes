# Planning for Priority and User Stories

Git Workflow for Group Projects:
1. Create group repo in Bison-2014 folder (public)
2. Everyone forks from that folder
3. git remote add upstream <link to group repo>
4. create pull request to group repo
5. do NOT merge any request until someone else reviews it, and then they merge it
6. Start from user stories
7. README is mandatory: group project name, github handle and names/twitter, description, how to install locally, how to use the app (not super detailed but verbose)
8. Contributing file: pull request and git workflow is explained
9. Code Style Guides: use the airbnb ones on the bison-2014 repo
10. Commit messages: this is public and people will watch them, be clear and appropriate
11. Link to Trello board on readme, public
12. Standups every two hours, retro at the end of the day
13. Wireframes, visual style guide
14. Use TDD
15. Using Travis CI and Simplecov
16. Deploy to Heroku immediately --> easier to handle issues without doing one giant commit to heroku
17. Do a manual commit, Heroku can be funny
18. Add bugs to the Trello board --> be as detailed as you can, can you repeat it, what browser/version, operating system, screenshots, etc. 

Process:
1. Start from user stories
2. Prioritize: what can be done first? what has other things depending on it?
3. Determine Minimum Viable Product
4. Remember we are not deploying for production, just for demo (also good to have demo in case something crashes before you present your program)
5. Figure out your waterline: at what point could we release it to real users (with some features unfinished)?
6. Relative work: estimate how long a feature will take and then check in at standup. We use a point-system is 0, 1, 2, 4, and 8. Avoid 8 point stories! 

Continuous Integration (Travis)
1. Runs all your tests every single time someone pushes
2. Combats regression bugs --> when one part of a code messes up another if you've only been testing that small bit of code
3. Knows about bundler and knows about rspec
4. Set this up ASAP

Simplecov
1. handles test coverage
2. computes the coverage of your tests for your code
3. put it in the rails helper right at the start --> it generates an html file that gives you your percentage

Demos (Check the github for more robust list of what is needed)
1. Needs to be from Heroku, not local
2. Show simplecov
3. Everyone talks about what they worked on, challenges they faced
4. Agile team practices

Trello:
1. Current - what is currently being worked on or waiting on a pull request
2. Backlog - based on user stories
3. Icebox - things that aren't on deck yet but if you have time for 