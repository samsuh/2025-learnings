# 2025-learnings

## Purpose
The purpose of this file is to track and measure the different topics and levels of learning accomplished over the year. Additionally it is a scratchpad and workspace for me to aggregate the different resources I found useful and that I want to revisit at a later date. 

## End of January

### Quantum Computing 
- Watching someone build a qc at home using lasers:
https://youtu.be/muoIG732fQA?si=iLFFr_RIAuqDQVb4
Thoughts: illustrates basic qc application using light and a prism. 

- Quantum Computing Basics video
https://youtu.be/tsbCSkvHhMo?si=AyzbY2ubXUhdMgrG
Started on Jan 28, 2025
Completed Jan 31, 2025 
Thoughts: It was a very well made course to introduce the various concepts in QC. I realized that I need better fundamentals in Linear Algebra. 

#### Linear Algebra Fundamentals 
Useful for quantum computing as well as AI/ML.
https://youtu.be/rSjt1E9WHaQ?si=N6Us_fWzsGPYv6ph
Started on Jan 31, 2025 
Status: Deprioritized.
This one did not work for me. I found a different Linear Algenbra tutorial to follow. 
Working through https://youtu.be/3Bf9oh7nkus?si=dG5tszsEYr0atskT (Korean guy with english voiceover) 
This one fell down hard on priorities as the NextJS course gained traction. I think this will continue to be backburnered. 

## February 2025

### NextJS
#### Udemy Course - https://www.udemy.com/course/next-js-the-complete-developers-guide/
Completed it last year, but going through it again with a better understanding of SQL and databases. The goal here is to get practice with the NextJS side but also to understand what exactly is happening on the database side. 
Completed on Feb 25, 2025
Thoughts: It's already going well, with more of the prisma ORM stuff making more sense. 
Progress: 

**Project**: Snippets

A few days in after helping host the bootcamp, I'm getting into the second project in the tutorial and it's making sense. There are some changes since Next14 that require some refactoring/adjusting. implemented the routing and rendering to homepage of the list of snippets. i went through another iteration of spinning up the nextjs project. got through initial setup, prisma setup, create resource page, creating the resource on the db, getting and rendering a list of all resources, and showing individual resource on its own page. Next I have to focus on building out the Edit page and then delete - it's a client component because it wants to use the monaco editor which requires both state and hooks. remember to use legacy install for monaco because it broke with Next15 ```npm install @monaco-editor/react --legacy-peer-deps ``` client components should be separated out into the /components directory to make them both reusable and keep things organized. The edit page makes sense, but im having trouble thinking of it from scratch. the props comes into the function, create an interface for typescript to take in the params from the url and wrap it in a Promise because next15 changed that. once it's there, create a components folder at src/components and create the editor as a client component to use hooks/state. server components for data fetching, client components for working with it locally using state/hooks. I cant seem to get rid of a warning message about awaiting params.id, which should be taken care of, but it might be a bug in nextjs15. i'll leave it and proceed. Put server actions into an /src/actions/index.ts file to organize and reuse server actions. running the server action from inside a client component is pretty complicated; can still do it by (1) binding the state to the function call, (2) watch for changes (anything besides form submission like onClick) and use startTransition to directly call the action with the new data. startTransition will make sure to update the data before navigating away. edit works, but it's not automatic/intuitive yet for me, so i will practice that part. Practicing it helps, but had to break it down into discrete steps. Not sure if i would know all the steps intuitively. Was able to get through most of the CRUD, but stuttered a few times on the next15 Promise syntax for accessing props, and the formData bind functions when calling a server action using data outside of the formData being submitted as in the deleteSnippet functionality. Almost there. Styling needs to be worked on too, but is a lower priority. Added error handling for form submission using useActionState in NextJS 15, which replaces useFormState hook from react-dom. it makes sense. not sure if i can do it all rote from memory, but the concepts are all clear. caching concept also clear, and simple using ```revalidatePath('/')```. 

**Project**: Reddit clone

Initial project setup: Install prisma, HeroUI (aka NextUI), and AuthJS (aka NextAuth). Perform initial setup. 
prisma schema setup including required schemas for auth flow 
heroui including setting up provider and picking it up from the next project
auth flow including setting up oauth credentials, callback route, and auth related server actions
adding data to database. defining the tables is really important to do right early. 
pulling wildcard info from the url is useful, and in next15 requires awaiting the params/searchParams 
using server actions to interact with the db is useful, and allows compartmentalizing the work between db client access, server action functions, and the actual page rendering. 
making reusable components like PostList in this project takes a lot of effort, and the pattern used here is to define server queries, and pass the actual query function down to children as props. then invoke the query from the child, wrapping the component in the parent with a react Suspense. PostList was reused 3 times: listing top posts in home, a single topic's posts in the topicShowPage and search results from using the header's search input.
- **TODO: Deploy live version. This requires migrating from sqlite to postgres (look into vercel/neon)**

### Databases 
#### SQL and PostgreSQL: The Complete Developer's Guide
Completed in January; mostly uses 'pg' and raw sql, using interpolation to sanitize. Good to learn and good to review how core sql works. but prob wont use it in projects directly. 

#### Prisma - I want to get more familiar/competent using prisma. It was good during the NextJS course, but a lot of that was premade for me, so I want to go through and build my own and create my own schemas and queries. 
- Youtube prismaORM tutorials
  - Done - travery media prisma video. he just shows basics, but doesnt explain the detailed interactions very well. it's good as a review if you already know it and know why things work the way they do. (https://www.youtube.com/watch?v=CYH04BJzamo)
  **- ByteGrad prisma in NextJS (https://youtu.be/QXxy8Uv1LnQ?si=1f_hI5i3tLc8t39X)**

# Areas that I should look further into
- **Look into google analytics, especially as a follow up to nextjs stuff. look into "next-ga"**
- **ThreeJS course. the goal is to get a nice looking frontend-focused, well designed, eye-catching site on the portfolio. Maybe something around motorcycles, like a motorcycle maintenance record keeper site (that tells you when service is due for different components)**
- **n8n is gaining traction to automate low-code workflows for agentic chaining. definitely scope how much i want to use this.**
 - **Cryptocurrency Development 
  -** Alchemy Solidity Course (go for certification) **
  -** Ethereum with Solidity, React & Next.js - The Complete Guide (The NFT Marketplace project) **
  - **Ethereum Blockchain Developer Bootcamp With Solidity (2025**

 ## March 2025

Objective: For March, now that I'm well into the flow of learning and doing, I need to better organize the roadmap of what I want to be working on, and getting a grasp of all of the dependencies and ancillary skillsets I will need to accomplish the new workflow. At the end, I want to have a regular routine of being able to capture ideas/tasks and build it into a workflow that helps me plan what needs to be done. This document is turning out to be one tool to capture and structure ideas.
- Start on trello clone implementation. Focus on database access as well as on converting to Next15. https://www.youtube.com/watch?v=pRybm9lXW2c
  - Host this somewhere. Initially host locally or on spare computer in home, but look to move this off to cloud or to set up a better dedicated home server machine.
    - This breaks down into: (1) deploying and maintenance (2) optimizing. I think optimization is low priority for now since I'm the only one who'll use it initially.
- Trello clone vs the Asana clone. https://www.youtube.com/watch?v=KAV8vo7hGAo
  - concerns about: using redux, the complexity of this project, the mui styling. the auth is not one im used to either. I think getting this done, then refactoring the parts into the tech stack i would want to use would be a good challenge. 
- Learn more about automated workflows; n8n and figuring out if n8n-style workflow makes sense, or if I only really need one or two workflows. If only a few, is it better to just build it in automatically into a workflow from scratch, or to keep using n8n workflows?


**Project**: Asana Clone 

- Go through the whole thing once to get a gist for how he structures things and implements things. I'm not familiar with this creator so I'd like to get a good idea of what he's doing, and what I would want to change on my own version.
- I'll likely go through this a few times through. First, to get an understanding of what he does, second to implement it his way myself, then again afterwards to refactor it to be how I would do it, then to start adding functionality to it and changing things around for my own needs.
  - Things I dont like about this way: In addition to the auth selection, using redux, he uses a NodeJS backend and a NextJS frontend. The reasoning is that NodeJS is more scalable as a standalone backend server, but I feel you lose a lot of functionality by decoupling the nextjs front and back ends. Reserve judgment, but keep an eye on this pattern. It makes sense, but there's little guidance on whether this is a good way to approach it. I guess it doesnt matter as long as it works for now, and I can refactor it later when I learn more. ReduxToolkitQuery seems unfamiliar, and might be a stumbling block in learning this project. His styling of the 'priority' is a nested ternary operator, which feels wrong. Maybe create tailwind css variables to solve it cleaner. https://stackoverflow.com/questions/64872861/how-to-use-css-variables-with-tailwind-css. His ListView component is really barebones, and can be improved a lot; having it collapsed to just the title by default with core information, and expanded upon clicking it would be a good upgrade to build in. The create form has room for improvment; can do better validation. MUI table functionality is pretty cool. Homepage projectId variability functionality missing. Hard coded in 'useGetTasksByUserQuery'. His priority display pages are all copy/pasted versions of the same thing. Worth looking into refactoring using dynamic routes. I stopped watching around the AWS part of the video, as it feels separate enough from the actual coding of the site, aside from amazon cognito for auth. I will go back and begin coding the project for my second pass through the material. Will start project after watching the aws part. Using lambda function just to pass the user trigger is wild, and that's so much configuration just to mirror the data across from aws to our backend.
  - yesterday I was ready to set off on coding this through, but today that motivation has completely disappeared. I think part of it is that I don't know exactly what I want to get out of coding along. The reduxtoolkitquery stuff is foreign to me, as well as the fact that a lot of the visual impact functionaltiy (drag and drop, and gantt chart) are separate react packages. I think what might be more useful for now is to diagram out a whole separate webapp that uses the stack that I want in the end, and then I can try to map out the routes, data requirements, and design it all on my own first, then maybe try to implement it all.
  - Oof. Ok so thinking this through, the separate nodejs server for the backend makes sense for large scale applications, but that's not what i need. it's for the viewers who want to be applying for jobs at large tech companies. I just need small applications that work as proofs of concept and scale up to mvp. I should stick to nextjs stack, but learn things better. the reddit clone project is great, but is basically an exercise in submitting forms and passing formdata around. I should go back and rewatch the sections focused on client-side reactive interactions.
- implement something simple like a drag and drop image into the form as a first incremental improvement. adding a user activity page would be a good way to create a page with data from scratch. maybe similar structure to Search page, but run multiple queries where the userId matches, return components listing the posts, and comments that the userId=authorId if that works. Return a count of various activity for the user, like x posts created, y comments created. PostList created successfully on the User activity page, but CommentList was not reusable like PostList was. CommentList takes in a postId, which is irrelevant for the way we need to work with the data. Trace back how PostList makes itself reusable, and do the same thing to CommentList to allow it to accept either a postId to render inside the PostShowPage as well as taking in a userId or abstract it out to take in just a query result of comments; watch out for the nested structure since we prob want to display the comments more like PostList.
  - User Activity Page is implemented and it fetches the posts and comments by the user. Could use better styling but it works for now. It's too open-ended as to what to do next. I could work on react-drag-and-drop stuff, which would ultimately be implementing something like a trello board. This would be useful eventually, but it doesnt make much sense in the flow of a reddit-clone. Alternatively, refactoring the reddit clone to be more like producthunt would have more usefulness as a real usable project sooner. Maybe I should try to sketch out the flow for coinfind again with a little more experience under my belt

My interest/focus/attention seems to sway between projects and initiatives. I feel like consolidating my focus and spending it all on a defined push would be the best way to spend it. Usually i use external cues from people to help me focus my productivity, but I'll need to figure it out on my own for now.
Critical thinking of actual projects is hard and uncomfortable. It's so much easier to just start another tutorial and feel productive, while not making much personal progress with the tools I already have some access to. 
- For now, when it's hard to decide what to do next, and if i dont want to start up another tutorial, another way to progress would be to get better at using the existing tools in the stack i like. So NextJS, NextAuth, Prisma, Postgres, maybe HeroUI or swap it out to shadcnui.
**TO DO: allow user to sign out and sign in using a new auth flow, instead of just signing them back in with the pre-approved first auth flow (so i can sign in using a different account)**
**TODO: refactor postShowPage to be uploadable in coinfind form by a team user.**
  - This might require expanding the User definition to include "team" or to have a separate "team" table or something like that to represent the projectTeam as a whole.
  - Would this require adding "tags" isntead of "topics" and re-thinking what "topics" means here? "Topics" might be closer to "Ecosystem" where they have to reduce down to a single ecosystem to attribute the project to. Maybe also introduce "tags" table to use to bridge over to different topics or "categories" that topics can all bleed into, such as "EVM".
- Creating a "Likes" table would be good practice for manupulating the data schema. One user can make make likes, one comment/post/topic can have many likes (how to make unique likes so you cant like multiple times). Should it be called likes or favorites or members or something.
- Read through docs:
  - AuthJS
  - NextJS
  - Prisma
I got sidetracked into n8n stuff. There's a really cool research workflow that I want to adapt for use in coinfind. 
I also got sidetracked by looking more into typescript stuff. https://www.udemy.com/course/typescript-the-complete-developers-guide/
Regarding all the other functionality I want access to, it might be worth looking further into NodeJS; things like accessing the os, or other standard libraries. 

Project Idea for Coinfind: 
- User comes to visit for up-to-date ecosystem information. user can get reports regenerated in the moment with up to date information pulling from many news and social media channels. Free tier and more detailed info that takes up more resources to generate payable by stripe or crypto both membership model and one-time-access/one-time-generation. General info but also automated technical analysis should eventually be available. Success metric to monitor would be how often people come back for updates. Sign in with metamask and other browser wallets should be a feature, and payment with those same wallets should be enabled. See if we can enable subscription-verification using the wallets. 

Getting more familiar with using Typescript, and looked into metamask implementation in nextjs. Metamask has an SDK but there's probably better alternatives since i dont see people using that sdk regularly. Typescript's main benefit is to make interfaces and classes work together predictably and consistently. The typescript course is fine for the fundamentals part, but the middle projects are a bit of a slog. I want to get through it though because I want to be able to build a web framework and don't want to miss anything. There are some helpful tidbits of ancillary stuff that's also useful sometimes. The most useful part of the typescript course is the usages of other useful packages and functionalities like using os in node to readFileSync, or using maps. interfaces/classes in typescript are not functions, so not directly relevant for server actions and other functions in nextjs. i'm hoping to see how they connect. Maybe skim nodejs docs or do a nodejs course soon. I got through a lot of the typescript course, but it's so boring. I cant maintain focus on it, and the overall state it puts me in is unproductive. It's funny because I lost steam around the same place as last time so it's not just a current-me problem; got through all the lectures, but the projects are so long and boring and unproductive and reptitive (oh so repetitive!) that the value is too low to maintain focus on. I think it's better to take a mental break then refocus on something more applicable and practical. The main takeaway from the typescript course was about the usage patterns. abstract out the minimally reusable part into a type/interface and have it be 'implemented' by other classes to make it consistent/reusable. types vs interfaces; types are fixed while interfaces can be extended

After reviewing the existing blockchain courses, I have decideed to do this one next. https://www.udemy.com/course/blockchain-developer/ the reason is that I like his structure, and this feels the most up-to-date as it was updated earlier this year. The goal for this course is to understand which wallets to integrate for ethereum web payments and ethereum authentication. I know there are other auth solutions such as walletconnect, metamask sdk, and clerk for a full solution, but I want to try to roll my own eth auth. maybe do something with authjs and a wallet. Started going over the blockchain course, got through basics, and the first mini project. The info is starting out very basic, which is nice, but his teaching quirks are standing out more than the course content, which is not great. His analogy of hashing using colors doesn't make sense and is confusing unless you already know exactly how hashing works, which would defeat the purpose of the whole analogy. colors dont combine in the same ways as hashes do, and that would just confuse newbies. Stepping back from the details of solidity/smart contract implementtions and security, thinking about the product again, I really only needed to have auth functionality with a wallet for now. Later iterations of the site can make better use of the wallet address for payment functionality or gating content by signing with a wallet with sufficient token balances. All i need for now is to associate a wallet address to a user in the postgres db, and allow for one user to authorize many wallets. Each signature or tx using the wallet will be independent, and not need the db User model to perform. Maybe subgraph it back in later. 

Additional functionality needed: 
- Research workflow
  - define what functionality will be offered in the MVP initial version, and backlog the rest into a roadmap. Core functionality is the 'summarize this project' free-tier general summary.
  - Users should be able to trigger a "rerun report"; this should be authorized only; either by user or require a wallet signature (later a payment should be required)
    - Where should this run? backend? Node? can this be triggered by a POST request? 
  - Research workflow should be defined and have multiple levels; Simple, Detailed, Trader
- n8n workflow is a missing piece for now. might be good to shore this up first before committing too hard into other areas.
  - I'll get through a few more eth dev lessons, get a better sense of what's available for ethereum wallet auth and making the account-to-userInDB associations, then switch to n8n
 
- Wallet-based authentication/signin seems to be best covered by walletconnect, since it allows for more comprehensive login than just a single wallet or method. (walletconnect rebranded to reown) https://docs.reown.com/

## n8n learning - Done for now
- course level 1 started. First mini workflow completed (hacker news workflow). "Nathan's workflow" created, http request sent, data inserted into airtable base. Next is filtering data.
  - "Congratulations, you completed the course and passed the quiz!" 3/19/25
- course level 2 started. it's much less engaging than level 1. only got halfway through the first part. it's very not engaging. got distracted and watched some videos on n8n intros, and MCP generally. also looked up that webhooks is prob the easier way to implement n8n to a nextjs frontend.
  - Completed, but took an extra day due to n8n's bad documentation. solved and documentation update recommended to n8n. goal for 3/20: course 2 and create a webhook that is triggered by nextjs. got past binary data. but unresolved issue is having to mount a volume to docker to give access to filesystem for n8n files. Got through data. errors next. errors require setting up a messaging system of some kind; discord/slack/email,etc gmail set up, trick was i had to add self to test users in 'audience'. The last workflow is frustrating because the discord node keeps erroring. it makes no sense why it's erroring. i think it's a problem with n8n's given webhook url itself. i cant even get it to send a simple text msg of "test" sometimes. 

## Implement something that executes everything at a basic level and brings it all together into one place. 
- Phase 1: Coinfind initial layout could target ProductHunt-style interactions where a project team or "supporter" can suggest the original project. Eventually this should be authenticated and verified, but for now let's just make it work.
  - Initial project submission: ProjectName, ProjectDescription, Ecosystems, Tags, SmartContractAddress?, URL?, Contact
    - Eventually we can do something with bounties or airdrops for first signups. We can represent this initially with CF-points to eventually be replaced by a token. Like Reddit karma or likes or whatever for now. 
  - Vote on new projects.
    - Have some CF-point interaction. Maybe initially lets just let the first 10 people claim a CFpoint for either up or downvoting. 
  - Comment on new projects. Also have some CF-point interaction.
  - Authentication needed for CF-points to track point balances. 
- Phase 2: Implement "research" automated flow
  - n8n workflow
  - nextjs trigger that can 'cost' some CF-points
update: I've been mainly focusing on n8n, and also taking a mental rest day from coding. Life seems to be going pretty well, and I want to look into NewSchool to get plugged back into community. The only event im really looking forward to is BUIDL Seoul's ai hackathon, but want to do other life balance stuff like riding, maybe traveling. These thoughts are on my mind, but it feels like automation and workflows that incorporate ai and stuff through MCP and that stuff is the current wave. I can already kind of see the end, but it shows how productive a single automater/developer can be and how much they can leverage existin systems.
Reinstalling postgres on my windows machine. not sure why it's not here anymore. Maybe lost it during the reset.

Perils of being "smart" as a self identity. https://youtu.be/U4PsIm9dDvs?si=2aXL1lcwrbr4cxR2

I find myself losing a lot of time. Motivation wanes a lot, and I can't make solid progress on my loosely defined goals. However, I don't want to "waste time" and I find myself going back to the comfort of making progress on video tutorials and courses. This is a crutch. I need to focus more on work output and not rely on the dopamine of learning things conceptually and being exposed to concepts over output. Learning is good, but learning in lieu of output is not good.
Spent some time exploring more about the trello clone tutorial on youtube. It's ok but he wastes a lot of time implementing his sponsored services like clerk or whatever. it is very dependent on lots of external services for no real reason. makes a lot of it not worth implemnting. At least it's nice that I'm not feeling completely lost on them, and im able to recognize what's core functionality vs what's directed fluff. 

I lost most of a week. I need something to tie me down to reality and the flow of time better than indepdnence. I will keep losing time if i don't have external time prompts keeping me aligned. 

Watched a couple tutorial segments, but that led me to wanting to learn more about React's Drag event, which led me to the javascript implementation. https://developer.mozilla.org/en-US/docs/Web/API/HTML_Drag_and_Drop_API

### Have a Beginner's Mind
I was watching a painting video, and she mentioned how trying to do too much too fast stifles growth. I realized I wasn't having much fun, and part of that was due to the fact that I kept getting stuck and having to go on a side quest to resolve the issues, but the frequency of those stoppages prevented me from actually getting into a flow state to feel good about programming. I plan to set aside my ego and go back to basics to cover some of the fundamentals that I may have skipped in the past. I will redo a thorough beginner course and really absorb the fundamentals while I'm doing it. I will collect the smaller projects into its own repo and keep my notes as I go as well. Ego is preventing my growth, so I will address it head on for the sake of getting better and hopefully being able to get better fundamentals. I'm hoping to solidify my fundamentals in various aspects: Vanilla Javascript and NodeJS to go deeper on the work I've done this year already on NextJS and Postgres. I should also take the time to shore up my skills on Data Structures and Algorithms while I'm in the beginner mindset. 
"Back to Basics" begun in its own repo for notes and learnings. https://github.com/samsuh/back-to-basics-javascript-2025

Random sidequest. Got asked to make a telegram bot in the style of a celebrity. Got it to work eventually. the bot portion is really simple nowadays. the hardest part was actually getting the connetions to work.

Beginner course in javascript is taking longer than expected, mainly because it's so slow, and I don't want to skip things. It's nice to revisit some basics like the difference between For-In and For-Of loops in javascript. For-In-Keys. For-Of-Values. There have been some other things that were good to know, but it does kind of feel like a waste of time. Doing easy things in video format is inefficient, because you have to rely on the delivery of the creator, and their choices on what to focus on and the level of detail they go into or skip, is inconsistent. But the alternative is just to go through docs one by one for every function and every little detail, so it's a balance. Taking written notes helps to focus the information a bit, and stay engaged. 

## April 2025 
Objective for April: Hackathon, finish 'back to basics' for javascript. implement something using n8n. Maybe go for coinfind first iteration before starting docker stuff to go for botlib stuff. 

Traveling around using a different computer gives me a chance to reset and rethink about my current coding setup. It also is a good way to see what i rely on regularly. I tried setting up auth using nextauth from scratch, but couldnt do it. It wasnt a big deal, but it's disheartening that after implementing it in so many places, it's clear that i dont know how to do it on my own, even with documentation. I know i have to set the SessionProvider, but it's not working. I didnt trouble shoot it in depth due to lack of time, but the fact that it wasnt easy sucked. I deviated from the prior tutorial because I did not install @auth/core@0.18.1 @auth/prisma-adapater@1.0.6 next-auth@5.0.0-beta.3 have to look into what difference that makes. 

NextJS Auth practce using AuthJS. 
- create a new github oauth application
  - set callback URL to http://localhost:3000/api/auth/callback/github
  - get clientID and clientSecret, and make up a authSecret string
- have to set up auth.ts file, which is the central point all the auth happens /src/auth.ts
  - import NextAuth, Github, {PrismaAdapter}, {db}
  - schema.prisma file had a lot of structure around auth. model Account, model Session, model User, model VerificationToken -- these are used by PrismaAdapter
  - access env variables, check for errors
  - call NextAuth with config object
    - NextAuth({ adapter: PrismaAdapter(db), providers: [Github({ clientId, clientSecret })] })
    - destructure this off the NextAuth call: export const { handlers, auth, signIn, signOut } = NextAuth({//alltheabove}).
      - handlers can be set to "handlers: {GET, POST}"
    - note there was a bug where the clientId is not returned. to handle, add callback to NextAuth object and set manually.
- set up app/api/auth/[...nextauth]/routes.ts file to handle requests between app and github
- make server actions for signin/signout

Trend observations in April: 
- "work" as a commodity
- decision-making and resource allocation as a value proposition; resource-enabled DAOs?
- ai website generation seems to be getting good for static sites. visuals and basic functionality, transferring data around.
- I want to think through the usefulness of botlib and see where there's an opportunity for it to exist/coexist in the ai ecosystem.

Coinfind: look up how RSS works and build an automated RSS GET workflow. (prototype now done 4/6/25)
RSS GET > Store > Process > Run Research > Store > Publish (pubsub?)

I want to figure out this auth situation to set up my environment to be really usable so i dont have to hit this roadblock every time i wanna do something. prep breaks down to a few separate steps: 
- i want to run postgres in docker alongside everything else. lots of docs are using docker compose, not docker desktop. figure out the difference. 
- one postgres is running fine, connect it into a nextjs project with boilerplate defaults, and understand them well. prisma adapter has required setup for different db types. different for postgres/mysql/sqlite/mongo
https://docs.docker.com/guides/databases/ it's running fine in docker container. need to be able to hit it with data writes/reads.
- once i have nextjs and postgres running, get nextauth to work cleanly.
- the end goal is to get everything configured in n8n so i can whip up workflows and have everything writing to somewhere more permanent and sustainable than an airtable spreadsheet for db storage
--> postgres in docker / postgres in nextjs / nextauth in nextjs+postgres.

status 1. so far, figured out the reason ive been having issues with docker desktop is that there are multiple vm instances running. Ubuntu and Ubuntu24.04 are different vms. "Ubuntu" thats the default is the one im running in docker desktop. but the 24.04 is whats running in wsl directly. need to resolve eventually, but will just go with "Ubuntu"vm for now. 
running postgres inside docker desktop should be straightforward similar to mysql or mariadb setup. watch out for the port assignments
status 2: try to get one read/write into postgres. done. docker desktop running postgres container. go into EXEC tab and run using psql. had some issues with user because postgres needs linux username and su user to have the same name. figure this out later. 

April 11-15 In Seoul for ETHSeoul hackathon. We built https://youtu.be/YLg7-xq7gBk?si=i6UQ570TQqAoKMxp file manager based on filetype. 
It's hard to network with people at conferences without a project to represent/ categorize myself into for people. 
JY had strong interest in a localized RAG for private materials like company manuals, and working with a knowledge base like RAG via chatbot. Accuracy was a high priority, so citing sources and not making up data is a priority. The main issue for her is that she's not technical at all, and would need this built out for an end user; making her setup docker, or hosting would be unrealsitic. 

## Potential Business 
I feel like one way to play this AI building is to build a devshop that solely builds ai workflows and handles client devops-as-a-service. basically just next-gen ai-enabled freelance dev. The first steps here would be building common workflow "templates" to offer clients. Then to find a shippable workflow; either self-host and give unique access or better but more complicated would be spinning up automated client-specific spaces for each client. 
- What exactly can i build
- How exactly does it look to deliver this for the client
- How should this be charged, and how much should be charged? 

Going back to review llm fundamentals: https://youtu.be/wjZofJX0v4M?si=zBG7rCIF3KZwCFzq Good video going through high level concepts. Good structure to the info. Good for working backwards through understanding the process. 

## Ethereum Protocol Developers Study Group
https://epf.wiki/#/eps/week0 
4/19/25 - Episode 0. 
4/20/25 - Ep 1 complete
4/21/25 - Ep 2 Consensus Layer
4/22/25 - Ep 3 Execution Layer. This one might take a few watches to absorb. Left off at around the 1hr mark after state transition function stuff. before the EVM stuff.
4/23/25 - Ep 4 first half. created discord server for community study group. 
Notes: Remember that these are to be done over a full week. consuming the videos one after another is probably not the way to go. However, there's many lectures in the week, so it's hard to know how much to get through per day. It seems like one lecture video per day of the week. There's a lot of additional reading that I havent been doing thoroughly; I've been skimming and getting through it for the sake of progressing through the rest of the content, but I'm definitely skipping over some content, and it's definitely not sticking as much as possible.

I feel a lack of purpose after the ethereum conference week. I am no closer to having an overall goal, or in having a developmental direction to pursue. I did get a tiny glimpse of flow state during the hackathon where we started coding and a couple of hours passed by before we were at the end of the day. I think maybe trying for a flow state while coding is still a good goal. I don't have a lot to show for the progress I made this year, and I'm still not good at anything yet. But consistency might be the key. 

taskangel site - bounty platform? deposit real money first to create a bounty. pay on completion if agreed. worker "i did the work" appeal. assigner "they did not complete work as agreed" appeal. 

4/21 - watched a townhall meeting for EPF and had a few thoughts. Im not sure im technical enough to qualify for EPF, but it's probably where I want to be in terms of committing more to a more technically-minded focus on ethereum. regardless of acceptance into the fellowship I should get through the EPFsg materials and get caught up to speed on technical developments and the ecosystem. I started reading vitalik's "potential futures of ethereum" booklet, which is good in conjunction with the EPFsg materials, as more of an overview/overarching vision/direction. 

## Started Rust Course
4/26 - Started Rust course. 
4/27 - got through overview of struct, vec, #[derive(Debug)] 
4/28 - got through arrays vs vectors, immutability of bindings by default, "{:#?} formatter" 

Getting caught up in the RISC-V EVM discussions. If I make it through to the Ethereum protocol fellowship, i'd be interested in focusing some effort into implementing part of this initiative, or contributing to it. Here's a chatgpt overview of the process I'd be looking at: https://chatgpt.com/share/680f8cc7-c1a8-800f-854e-1c89569f8651

4/29 - rust implementations and implicit returns
4/30 - rust methods using &self, and using crates 

## May 2025
5/1 - 3b1b released an interesting video on grover's algorithm for qc. https://youtu.be/RQWpF2Gb-gU?si=ezz1LyNbqFJbZt3j.  the takeaway is that quantum computing does not turn NP problems into O of 1 time (it does for very specific situations), but generally it is a sqrt(n) time. This is because instead of parallelizing everything at once, it ratchets up the state vector towards the target solution-vector by theta (the amt of correctness in the state vector at the start) every time through. very cool visualization of how qc speeds up problem solving. 

Back to Rust learning

5/1 - rust. started getting into ownership/borrowing/lifetimes. 

5/2 - Rust wants to eliminate unexpected updates to data. 
- Ownership and Moving: the goal of ownership in rust is to limit the ways you can reference and change data. Many read-only references are ok. Every value in rust is "owned" by one owner. Reassigning this variable changes its owner by "moving"; moving makes the old one inaccessible, including partial moves. using a value in a function, even printing it, requires ownership to be moved to do so.
- Borrowing: act on a reference to the value using &value (technically, it's referencing the owner of the value). can also require an argument type to be a reference to a cerain &Type. could theoretically also return values, re-assign to the prior binding, and keep it available manually. this pattern is inefficient, just use borrowing. Read-only references are immutable (&value), writable references are mutable (&mut value), and can be used to change referenced values. Cannot create &mut if an & already references the value. Cannot change values via owner if a ref exists to it. Copyable values make a copy instead of tranferring ownership (numbers, char, bool, tuples/arrays if filled with copyable stuff, references (both & and &mut)

5/3 - Lifetimes. How long an owner/reference exists before memory is reclaimed.
- When an owner goes out of scope, the owned value is dropped from memory. there can't be references to the value when owner goes out of scope. Lifetime annotations are for managing relationships between lifetimes.
The difference in programming in Rust is that everything needs you to think ahead of time about whether it's taking ownership or not, whether we're using the value, or a reference to a value, if it's immutable/mutable, what it returns, and the same for any time we store data we have to think about values or references.

Considerations for simple Bank/Account structs in Rust. Methods are tied to an instance of the struct, AFs are on the struct itself. 
Argument type decisions. Store value somewhere? Take ownership. Do a calculation with the value? Take immutable ref. Need to change value? Mutable ref.
| Bank Description | Method or Ass.Fn | Name | Args | Returns |
|:-------------| :--------------: | :---: | :---: | :-----: |
|Create an instance of a Bank | Associated | new() | none | Bank |
|Add an Account to list of accounts | Method | add_accounts() | account: Account | none|
|Calculate total balances of all accounts | Method | total_balance() | none | i32 | 
|Create a Vec containing summaries of all accounts | Method | summary()| none |Vec\<String> |

| Account Description | Method or Ass.Fn | Name | Args | Returns |
|:-------------| :--------------: | :---: | :---: | :-----: |
|Create an instance of an Account | Associated | new() | id: i32, holder: String | Account |
|Add given amt to account balance | Method | deposit()| amt: i32| i32 |
|Remove given amt to account balance | Method | withdraw()| amt: i32| i32| 
|Print balance and holder as string | Method | summary() | none | String |

5/4 - Rust Enums. Think of it like "types" of structs with different variants selectable, like a Media enum with book/movie/audiobook inside. Without enum, we would have to have 3 structs, with 3 impls. With enum, you can have one Media enum with one Media impl with logic to check which variant youre working with. Pattern matching, "match" works logically like an if/elseif statement checking which enum variant "self" is. Note, we're not adding ';' to use implicit return, since we return a String. Use enums if the different things have the same methods; if the methods are more different use different structs (enums are called the same thing and return the same type). Also if each thing is pretty complex, might be good to separate into its own struct. 
```rs
match self {
  Media::Book{title, author} => {format!("Book: {} {}", title, author)},
  Media::Movie{title, director} => {format!("Movie: {} {}", title, director)},
  Media::Audiobook{title} => format!("Audiobook: {}", title)
}
```
Cool video walking through reth (rust ethereum) line by line: https://youtu.be/gPQ-uXj03iQ?si=7dxP518SnpXdz5DU
I plan to tackle this once i finish rust fundamentals in abt a week.

5/5 - Enums continued. enum variant can take required values in {field_name: String}, or just the raw type but using parentheses (u32), or nothing at all if it doesnt have attributes. 
```rs
enum Media {
    Book{title: String, author: String},
    Movie{title: String, director: String},
    Audiobook{title: String},
    Podcast(u32), //less clear what this number means to others, but could make sense in other contexts later
    Placeholder
}
```
- Rust does not have null/nil/undefined. It has a built in enum called "Option" that can be "Some" or "None". Have to access Some/None via pattern matching or "match" statement. 
```rs 
enum Option {
  Some(value),
  None
}
```
Different ways to use Option enum: 
- `match` on Some and None, handle both cases (best most thorough)
- `if let Some {} else {}` handle both cases
- `item.unwrap();` if item is Some, return Some. if None, panic! useful for quick debugging and common for online example code. 
- `item.expect("value should be here");` if item is Some, return Some. if None, print debug and panic. Use when you want it to crash on None.
- `item.unwrap_or(&placeholder);` if item is Some, return Some. if None, return default placeholder. Use when you want the fallback.

I feel like I'm progressing too slowly. I need a better routine to funnel information into my brain and keep it there. Progress is actually not bad looking backwards, but part of me feels like I'm leaving a lot on the table every day, and I need to up the intensity, as long as I don't burn out from it. Maybe a more balanced intensity but with more dedicated time off would work. 
Started reviewing data structures and algorithms to add some more learning/practice into the mix. Rust doesnt seem to be a good language to do DSA in. 

5/6 - Rust Modules. Organizing code. There are different ways to implement modules. 
First way of doing modules: create in same file. good for organizing a massive file that you dont want to break up. Note the `pub` keyword since everything inside modules is private by default. 
```rs
mod content {
  pub enum Media {/*fields*/}
  pub struct Catalog {/*fields*/}
}
fn main() {let catalog = content::Catalog::new();}
```
Second way of implementing modules: create a new file with the module name dot rs. This way is good for extracting functionality out into a modules file, but it doesn't need to span many files. 
```rs
// content.rs
pub enum Media {}
pub struct Catalog {}
// main.rs
mod content;
fn main() {let catalog = content::Catalog::new();}
```
Third way is the most common way in the wild. Spread functionality into new folders as well as files. Folder+mod.rs make their own module. the content folder's mod.rs file has to import everything from the folder and make it public so it's accessible elsewhere. use `use super` to reference the parent directory to import mods around in sibling level files. 
```
├── src
│   ├── content
│   │   ├── catalog.rs
│   │   ├── media.rs
│   │   ├── mod.rs //note this is required to be put inside the module folder
│   ├── main.rs
```
```rs
// content/mod.rs
pub mod media;
pub mod catalog;
// content/catalog.rs
use super::media::Media;
pub struct Catalog {}
// content/media.rs
pub struct Media {}
// main.rs
mod content;
use content::media::Media;
use content::catalog::Catalog;
fn main(){let catalog = content::Catalog::new();}
```
5/7 - holiday. Messing around with Results enum for error handling. Use panic if it's a program breaking error or completely unexpected. use Result to handle cases where you know it might succeed or fail.
```rs
enum Result {
  Ok(value), //use when something goes well
  Err(error) //use when something bad happens
}
```
5/9 - more on Result enum and error handling. The Result enum returns either something of the Ok variant or Err variant. Err is the name of the Result variant, but Error is a struct from the std library imported by the struct definition `use std::io::Error`. Calling `Error::other("reasonforerror")` creates an instance of that struct. Rust does not have a default "error" type built in like other languages. Each library has their own implementation of "error" or you can write your own. 
Calling the function that will return the Result variant isnt a direct call. You have to handle the `match` cases. If the success case returns nothing, convention is to return an empty tuple `()`. A tuple in rust is like an array of a fixed length with no labels, where the arguments are passed in a specific order representing a specific thing; like `type Rgb(u8,u8,u8)` where it can be used later by `fn make_rgb()` taking in red/green/blue values in that order. To pass in empty arguments, you can use `_` or `..`, the difference seems to be underscore ignores one thing, whereas dotdot covers "all the rest" so can ignore everything. 

5/11 - Stack vs Heap in rust. Stack is for fast small memory (2-8 MB), Heap is for growing potentially large things (GBs). "Data Segment" (Read-only data, static data) are literals hard coded into source code like `let num = 45;`. Generally, stack stores metadata about the data while the heap stores the data itself. 
Strings in rust. "String" vs "&String" vs "&str" (string slice). &str does not need anything from the Heap, it can point directly to the data segment's literal value. `color.as_str()` it can also create a ref to portions (a slice) of an existing string.
```rs
let color = "red";
let portion = color[1..4]; //take color from index 1 up to but not including index 4 (3 letters total)
```
- use String when you want ownership of the data, or if it has to grow/shrink (the other 2 are read-only). uses both stack and heap. 
- use &String rarely since it uses &str under the hood
- use &str when you dont want ownership of the data, or want a portion. uses stack and data segment. 

5/12 - Finishing up error handling section in different ways: nested matches to capture the Ok/Err variants (messy) / text.expect() to panic out (good to debug but dramatic error) / "try" operator `?` at the end if it returns a Result object. If `?` operates on an `Ok()` it automatically unwraps contents from the Ok. If `?` operates on an `Err()` variant, it also unwraps the contents, but returns out of the fn early. 
You can return a Result from main(). `fn main() -> Result<(), Error>{}`
- Use nested match statements when you want to write to meaningfully handle the error, like handling a default scenario. 
- Use .expect() .unwrap() for quick debugging or if you want to crash out of the program on error
- Use `?` try operator when you dont have a way to handle the error. No default/backup case. 

5/13 - Rust Iterator `.iter()` is a completely separate instance of a struct that lets us walk through every element of iterable data. `.next()` manually walks through the data.
For loop would work, but rust tends to use an "iterator adaptor" (like `.map()`) and "iterator consumer" (like `.for_each()`) pattern. Call .iter() on an iterable to create an iterator, but nothing will start iterating automatically until you either call .next() or an iterator consumer (something that calls .next() for you like .for_each()). 
```rs
elements.iter().for_each(|el| println!("{}", el))
```
5/16 - Iterators just arent getting into my brain. Maybe it's the explanation or the concept itself. It seems straightforward; iterators are a way to iterate over data that is serialized. The way rust does it is to create a new data object whose sole purpose is to iterate over some existing data. It has a few fields, basically it does things to point at the start/current/next/end of the iterable data and is accessed by certain patterns; using 'iterator adaptors' and 'iterator consumers'. 
I'm going back to the rustbook to reference their explanations. https://doc.rust-lang.org/book/ch13-00-functional-features.html
- Closures get info from the scope in which they're defined, so they can have access to values in context based on where they're called. 
- Iterators are a separate piece of data defined so we dont mess with the original. 
- Iterator adaptors are methods on the iterator that dont consume the iterator, but produce different iterators by changing something on the iterator, like `map()` will act on an iterator to change each iteration and return the changed iterator. adding an iterator adapter step will process what comes before it in some way, before eventually handing it off to a consumer.
- Iterator consumers take ownership and use up the iterator, making them unavailable for further steps. anything that calls next() consumes. Iterators in rust are lazy and dont start iteration on their own on creation. using iterator consumers is a way to start iteration. 

Start with a serialized piece of data. Create an iter from it. mutate data by creating a changed/adapted iterator (can chain multiple for complex stuff). eventually consume the iterator. 

got rejected from EPF. i guess i have a long way to go still. dont take it personally, but as an assessment of delivered content. refocus on delivering stuff, instead of learning stuff. start to wrap up learning in the next couple weeks and shift gears to production. Define scope, Produce, Deliver, Assess. Back to rust. 

5/17 - &Vec<String> (reference to a full vector of strings) versus &[String] (a reference to a portion of a vector of strings). &Vec<String> works fine when working with the whole vector, but if you only want a portion of the vector to process using full references, you have to create a whole new vector and reference that; better to use a vector slice, which references parts of the original vector. vector slice syntax is &[data_i_want] like `&colors[1..3]` which gets elements at index 1 up to but not including index 3. Taking in a vector slice works with both full reference and partial, so it's more flexible. 

.iter vs .iter_mut vs .into_iter
- .iter() gives a read-only reference to each element in the new iterable.
- .iter_mut() gives a mutable reference and
- .into_iter() *can* give ownership to each element in the iterable created. Rust convention is that `into` functions will take ownership. `.into_iter()` takes ownership when called on the value itself `colors.into_iter()`, but acts differently when called on a reference or mutable ref; this `into_iter()` fn does not take ownership in the case when it is called on `&colors` or `&mut colors` itll give back the same thing; either a reference to each value or mutable reference. 

.collect() is an iterator consumer. Be careful with the type of value you collect everything into when using .collect(), since collect can be used with many different types of data structure inputs and outputs. Collect uses type annotations on what calls it to figure out what type it should return (if it's the last thing before fn returns). so if our function expects to return a Vec<String> that's what the collect fn will try to make. can also specify inline `.collect::<Vec<String>>()` or can rely on type inference to know it should contain strings `.collect::<Vec<_>>()`

5/18 - finishing up iterators in rust. 
`.find()` is an iterator consumer that takes in an element and applies the closure until it finds one that returns a truthy value, and returns that element wrapped in Some(value) or None if it finds nothing. 

5/19 - on my morning walk, ive been thinking about how i can bridge the gap between learning and making. I believe it's because I don't have a solid enough mastery over the basics. I **understand** the basics, and I can work with it if i see it, but I don't have a solid grasp of how everything connects on a blank page. I have followed several tutorial patterns that i could theoretically repeat by copying, but it's not internalized as a part of me. I think I need to do it a few times, then teach it to someone else to internalize it. I should make a tutorial lesson for the sake of learning things myself; the side benefit would be that it might help someone else later. 
Rust. 
`.map_or()` is run on an Option enum that handles the None/Some cases. it takes 2 arguments, the first is what happens when None, the second is a closure that runs when Some. `.map_or(String::from(fallback), |el| el.to_string());`
`.filter()` takes a closure and applies a closure to every element, keeping the true ones, ultimately returning only all the true ones. 

Lifetime annotations: `'a` and `&'a` used with fns, structs, enums, and more.
a "lifetime" is the duration of time from when we define a value until it either goes out of scope or we move the value out of it. 
Rust makes an assumption when we have multiple reference arguments and we return a reference; it assumes the returned ref must be one of the argument references. 
Rust also does not read the code body to try to understand where the returns are coming from; <- this is why we must make lifetime annotations for rust. 

`'a` is just a convention we could call it anything like `'LifetimeAnnotation`. 
```rs
fn next_lang<'a>(languages:&'a [String], current:&str) -> &'a str {code body here}
```
The return 'a is telling rust compiler that the return &str is the same as one of the `languages:&[String]` references, and differentiated as not one of the `current:&str` reference. 
Lifetime annotations help code readability by making clear which input argument ref is going to become the output ref. 
If receiving only one reference argument and returning a reference, rust assumes you're returning the argument reference. However, when taking in reference arguments and returning a reference, always have to be mindful of lifetime annotations, even if we can omit the annotation itself. 
- Take in one reference and any number of values, returning a reference. Omit OK. rust assumes return ref is the one argument ref. 
- When writing methods (takes in &self), any number of references, any number of values, returning one reference. Omit OK. rust assumes return ref is the &self. 
"Elide" = Remove/Omit
"Elision" = Removal/Omission 

if you take in 2 ref arguments, but the nature of the fn could return either one, mark both argument refs as `'a` so the return ref knows it can be either of them. 

5/20 - Rust Generics 
writing a decimal number in rust defaults to a f64. to do something else, add a type annotation.  `let a: f32 = 3.0;`. cannot do arithmetic between different number types like f32+f64 does not work, same for adding f32 and i32. 
- typecast using `as` like `let a2 = a as f64;`
- num_traits crate: `use num_traits::ToPrimitive;` and `let a2 = a.to_f64();` but it returns an Option, so unwrap it. `let a2 = a.to_f64().unwrap();`
Generics let you generalize what exact type you pass in so it can work with different types. `<T:Float>` in this scenario allows us to use f32 or f64. Convention is to use <T> to mean 'generic Type', then <U>, but also people use <K> for 'key' and <E> for 'element', but it's just a convention. Name them usefully for yourself.
the `<>` contains a generic type, which is like an argument list but for types. `<T: Float, U: ToPrimitive>` 

```rs
fn solve()<f32: Float> (a: T, b: T) -> f64 {code body};
fn main(){
  let a: f32 = 3.0;
  let b: f32 = 4.0;
  solve::<f32>(a, b);
}
```
this code assumes a and b are both of the same type, and calling solve::<f32> means the type is f32. this isnt strictly necessary, and can be inferred by rust; it'll work without the explicit type declaration.
in the above, `Float` is a trait bound. A trait is a set of methods, like a class definition. It can have "abstract methods" (code not defined, just exists, which we have to define ourselves later) and "default methods" which have a default implementation already that we can use or redefine if we want to later. Using the trait bound Float means anything we pass in should satisfy Float, and then we can do anything to the argument that Floats can do (like `.powi(2)` it)
- We could also use more than one generic type, like `fn solve<T: Float, U:Float>(a:T, b:U) -> f64 {code body}` this means that the two arguments could be different types, as long as theyre internally consist with themselves, and having them both be Float means one can be a f32 and the other a f64 and work fine. This is different than having only T:Float without the U:Float because with only one, it cannot be both f32 and f64 at the same time.
- In this code, we can generalize by making it `<T:ToPrimitive, U:ToPrimitive>` since all numbers are satisfied by type `num_traits::ToPrimitive`. 

```rs
trait Vehicle {
  fn start(&self);
  fn stop(&self){
    println!("Stopped");
  }
}
struct Car {};
impl Vehicle for Car {
  fn start(&self({}
    println!("Start!")
  }
}
```
this makes the struct Car a Vehicle type that can do what Vehicle types can do. 
```rs
fn start_and_stop<T: Vehicle>(vehicle: T){
  vehicle.start();
  vehicle.stop();
}
fn main(){
  let car = Car{};
  start_and_stop(car);
}
```
Here, type <T> must be something that implements the Vehicle trait, so anything we pass in to the 'vehicle' argument must be type Vehicle, so vehicle and do anything Vehicle types can do. 
Completed Rust Course; I still want to review the last bit about traits again, but generally it went smoothly. I have a good grasp of the basics, and just need lots of practice. Takeaways are that rust cares a lot about focusing on types, ownership/borrowing. I need to find better examples of where/how to apply this in the real world. 
Rust To Dos: 
- Rust/Wasm game course I want to get through later
- Reth line by line walkthrough video

5/21 - Changing gears taking a step away from low lvl rust stuff to focus back on filling in gaps of my web development skillset. I am pretty confident on my webapp building skills, but weak on hosting, devops, and the workflow of hosting apps online. I will focus on a different course learning docker and cloud deployment ci/cd stuff. I plan to later circle back and deploy all the projects I have locally, maybe spending some time to go back and update them along the way. This will result in more tangible 'development history', maybe I can aggregate them into a developer portfolio as well. 

Reviewing Traits in rust. 
Creating a generic struct will let the struct take in different types of data, making it reusable. To do that, declare `struct NameOfStruct<T>` in the struct and itll use that type throughout, but also in the `impl<T> NameOfStruct<T>` the first one after impl declares the generic type, and the `NameOfStruct<T>` references the declaration. 
We made structs that can take in a specific type of item (String), then we generalized it to take in any type of item (Strings, numbers, etc) but once it's created it can only ever take that type. Trait would make it so anything can be taken in, and changed to anything as long as it satisfies the Trait. Use the Container trait with syntax `impl<T> Container<T> for Basket<T>`. This can only take in the fns/methods defined in the container and we cannot add more. Additional fns to Basket would have to be in a separate impl block without the `Container<T> for`. 
It makes sense, and it works. But again, I would need a lot of practice using this to internalize rust as a whole.

5/22 - Shifting gears off rust and to devops stuff with the end goal of getting more comfortable deploying nextjs apps on cloud servers. This in turn has the further goal of getting prior work into a presentable form that's organized, isntead of in scattered github repos (some private), and getting them deployed and usable. For now, focus on creating a deployment workflow in place, and then go back and update the old projects' content afterwards. 
5/23 - docker stuff is more like review at this point. flying through the tutorial, but i think it'll slow down once i hit the actual devops stuff after the basic docker review
5/24 - feels like there isnt much to commit yet for docker review materials, since there isnt much code, and the docker files are all pretty local. maybe i should create a 'learning' repo and put all the code up, but that feels excessive for small things. 
Docker compose restart handling in the docker-compose file: this must be put on individual services in the docker-compose file, and can mix/match different policies on different services.
`restart: always` alternatively `restart: "no"` (note the double quotes which are required), `restart: on-failure` (any error code other than `0`), `restart: unless-stopped` will try to restart unless we the dev stops it manually.
Workflow using docker
- docker for development
  - "Dockerfile.dev"
  - dont put node_modules in the docker image
  - `docker run -p 3000:3000 container_id`
  - for hot reloading, instead of using a snapshot of the actual source code to build an image, use docker volumes to reference the source code to be built.
`docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app <image_id>`
    - note: the -v creates the volume, but we can bookmark a folder in the image, or reference outside the image on our local dev machine using the ":". first -v says "dont mess with the node modules folder" and the second one says "reference everything in the app folder".
    - can simplify this by using docker-compose instead of a multi-flag run command. 
```yml
version: "3"
services:
  web:
    build:
      context: .
      dockerfile: Dockerfile.dev
    ports:
      -"3000:3000"
    volumes:
      - /app/node_modules
      - .:/app
```
run using docker compose. `docker-compose up`

5/25 - web development workflow using docker. react (node) site. 
- to run a node server container with tests, there's a few ways to do it, no ideal ways if you want to actually interact with the test suite. 
  - `docker-compose up <app>` but this does not hot reload if we change tests
    - add `docker exec -it <appid> npm run test`, and this works if you need to use the test suite directly, but need to remember to run the additional exec cmd. 
  - edit docker compose yml file to run two containers: one for the webapp and one for tests. pretty much the same, but change the `command: ["npm","run","test"]` and dont need port binding. this has the drawback of putting our testing outputs into the same terminal as the server, and also we don't have stdin input ability. we can try "attach"ing to a running process, but it won't work here because it will attach to pid 1, which is "npm" not the actual "npm run test", and there's no real way to drill into the testing suite itself.

docker web server production build. replace the node dev server with nginx for production. 
- the thing is that for production we want to already use a base image of node:alpine, but we also want to have nginx running on it as a base image. this can be solved by using a multi-step build process.
- step 1: build the react project. use node:alpine -> copy package.json -> install dependencies -> run npm build. this results in the built project
- step 2: build the nginx process. use nginx -> copy the built folder from step 1 -> start nginx. note this only keeps the folder from step1 and doesnt use the rest.

In `Dockerfile`
```yml
  FROM node:alpine as builder
  WORKDIR '/app'
  COPY package.json .
  RUN npm install
  COPY . .
  RUN npm run build

  FROM nginx
  COPY --from=builder /app/build /usr/share/nginx/html
```

then `docker build .` which builds from npm, then goes through nginx step, copying build folder over then runs nginx to build the nginx image with the built website files on it. 

then `docker run -p 8080:80 <img_id>` then open browser to localhost:8080 to view the site running from the nginx container 

-> next step would be to host these containers on cloud servers

CI/CD workflow 
- Create github repo for the project
- Set up Ci pipeline using either travisci or github actions: triggers (when to run) > jobs (what to do) > steps (how to do it) > actions (reusable units of code)
- Set up aws. elastic beanstalk good for running a single container. Change it for multi-container deployments later.

5/27 - got multi computer development and build steps working. Next is to deploy and be able to deploy from multiple places.
Got deploy to work. Man that was harder than expected, so many little configuration settings that need to be exactly right. I doubt I can do this from scratch on my own without constantly referring back to the walkthrough workflow. 
That was a lot of effort just to get the default react project deployed haha: http://frontend-env.eba-w4ifgtgr.us-east-2.elasticbeanstalk.com/

5/28 - wont get to code much the next few days, but i'll update to keep the streak going. the current learning focus is still devops and doing a multi-container deployment with the larger goal of getting up a dev environment for various projects to speed everything up using a dockerized ci/cd workflow. i keep feeling a painpoint that im not organized enough, and i have gripes with simple solutions like trello boards being oversimplified. i want to build my own trello board and customize it for the way i need it to be without worrying about re-organizing things into "projects" or "workspaces" or "organizations" or whatever. i just want lots of boards to move around and organize, then click into them to see different workflows and associated content. almost like a mindmap. is there anything out not that creates a collaborative mindmap? i looked into it a bit but what i want is a little different. i want a collaborative working canvas but that can be drilled into to open up into various new 'views', including a 'to do list view' or a 'trello board view' or 'timeline view' or something. the info in each thing should eventually be able to be summarized into a 'dashboard' view or even into a 'task view' that can then be worked with like a standard asana or similar. auto-extracting from the brainstorming view into a draft version of a workflow. 

5/29 and 5/30 in seoul. wont be coding much but good to review
5/31 back to it. 

## June 2025 
Last month was spent focused on learning Rust, and getting the basics down. This month I plan to shift focus to a practical development workflow, which includes a ci/cd pipeline using docker and github actions to build a site, then host it on a cloud provider (havent decided which yet, maybe aws, maybe digital ocean or something). By the end of June I should have a react or nextjs app in development that automatically updates itself when the github main branch is updated. If this is all done, I want to spend some time thinking up a product management brainstorming webapp; like trello, but for brainstorming and collaboration. 

6/1 currently practicing on a toy project that has multicontainer deployments that update themselves automatically on change. rn working on the development side using a Dockerfile.dev only, and once everything works in dev, can try to move to prod.
Workflow: Copy over package.json file, run npm install, copy over everything else, docker-compose file should set up volumes to share data across the multi-containers. 

there are three apps, client/server/worker. each one needs their own Dockerfile.dev. Here is the one for client: 
`Dockerfile.dev`
```Dockerfile
FROM node:lts-alpine
WORKDIR '/app'
COPY ./package.json ./
RUN npm install 
COPY . .
CMD ["npm", "run", "start"]
```

`docker-compose.yml` version of docker compose to run, and start of "services" section which will have postgres/redis/"server" which is our backend server. Array elements are shown by using a '-' in front. 
```yml
version: '3'
services:
  postgres:
    image: 'postgres:latest'
    environment:
      - POSTGRES_PASSWORD=postgres_password
  redis:
    image: 'redis:latest'
```
`docker-compose.yml` continued. 'context' acts as a filepath in our filesystem that has the root folter and drills down into /server. 'volumes' will leave the node_modules folder alone, but for everything else, whenever we reach out to '/server' it is treated as '/app'
```yml
  server:
    build:
      dockerfile: Dockerfile.dev
      context: ./server
    volumes:
      - /app/node_modules
      - /server:/app
```
later renamed service "server" something else to prevent naming collision
for environment variables, in development, this works but this feels super insecure if unchanged to production: 
```yml
    environment:
      - REDIS_HOST=redis
      - REDIS_POST=6379
      - PGUSER=postgres
      - PGHOST=postgres
      - PGDATABASE=postgres
      - PGPASSWORD=postgres_password
      - PGPORT=5432
```
someone mentioned that there's a more secure way of doing it: 
```yml
server:
  env_file:
    - server.env
```
or by running it in the docker run command `docker run --env-file ...`

finish up the docker-compose.yml file with the config for client/worker services: 
```yml
  client:
    build:
      dockerfile: Dockerfile.dev
      context: ./client
    volumes:
      - /app/node_modules
      - ./client:/app
  worker:
    build:
      dockerfile: Dockerfile.dev
      context: ./worker
    volumes:
      - /app/node_modules
      - ./worker:/app
    environment:
      - REDIS_HOST=redis
      - REDIS_PORT=6379
```
we will use an nginx server to distinguish http requests to the client or to the server based on requests to "/" or "/api/". `default.conf` is where we'll add settings to an nginx image. 
there will be an upstream server (server behind nginx) at client:3000 (default CRA port) and server:5000(we set default port for express server listening on 5000) "client" and "server" are what we called the service names in docker-compose.yml. then we'll listen inside the container at port 80, and if a req hits '/' send to client or if '/api' send to server.
renamed 'server' service 'express' to prevent potential collisions later. 
```
upstream client {
  server client:3000;
}
upstream express {
  server express:5000;
}
server {
  listen 80;
  location /{
    proxy_pass http://client;
  }
  location /api {
    rewrite /api/(.*) /$1 break;
    proxy_pass http://express;
  }
}
```
upstreams redirect incoming "location" rules to either client:3000 or express:5000
rewrite takes /api/whatever and chops off the /api/ to give /whatever. `$1` refers to whatever regex was matched by `(.*)`

troubleshooting errors:
- error: running into issues using docker volumes on windows. `npm ERR! enoent ENOENT: no such file or directory, open '/app/package.json'` this is a volumes problem that should not be happening on WSL native stuff, but it's happening anyway. i need to dive deeper to figure it out https://docs.docker.com/engine/storage/volumes/#mount-a-host-directory-as-a-data-volume
fixed. i was missing '.' in volume mapping in front of '/client:/app' shouldve been './client:/app'
- error: `nginx-1     | nginx: [emerg] host not found in upstream "express:5000" in /etc/nginx/conf.d/default.conf:6` i think that's because i named it express instead of 'api'. will check this next.
fixed: has to be consistent across the upstream server names, the `location /api proxy_pass http://name` (i had this wrong), and the docker-compose file that names the services before getting mapped via the context.
- i was hitting another error about a 502 gateway, but it was my own mistake. the same as the above error missing a '.' before '/client:/app' i did the same mistake for './server:/app' too.

the app is now in a pretty good state. can clean up for production, then deploy to aws

6/4 - spent some time messing with github action secrets config. i was doing it wrong. i need to put it under 'repository secrets' not 'environment secrets'. i got it to work. next step is to get this deployed onto AWS EB. for multi-container deployments on aws, we need a specific file `Dockerrun.aws.json` to tell aws how to handle the multiple containers and which ones to run. 

6/5 - apartment hunting took all day

6/6 - aws multicontainer setup
Old v2 way used `Dockerrun.aws.json`, but v3 does not need that file anymore, and can be done from `docker-compose.yml` 
```yml
version: "3"
services:
  client:
    image: "samsuh/multi-client"
    mem_limit: 128m
    hostname: client
  server:
    image: "samsuh/multi-server"
    mem_limit: 128m
    hostname: api
    environment:
      - REDIS_HOST=$REDIS_HOST
      - REDIS_PORT=$REDIS_PORT
      - PGUSER=$PGUSER
      - PGHOST=$PGHOST
      - PGDATABASE=$PGDATABASE
      - PGPASSWORD=$PGPASSWORD
      - PGPORT=$PGPORT
  worker:
    image: "samsuh/multi-worker"
    mem_limit: 128m
    hostname: worker
    environment:
      - REDIS_HOST=$REDIS_HOST
      - REDIS_PORT=$REDIS_PORT
  nginx:
    image: "samsuh/multi-nginx"
    mem_limit: 128m
    hostname: nginx
    ports:
      - "80:80"
```
- `image` is the image we made on our docker hub
- `hostname` is what other containers can refer to this container as like http://name 
- port mapping
- container link between "nginx" to each "client" and "server" is now automatically handled by aws. dont need to manually create links between containers.

6/7 - mostly offline today, but will review the aws setup. the aws ui has changed, so need to figure out where everything is in the new ui. didnt get much reviewing done. 

6/8 - set out to get the aws deployment done today. surprisingly i got it to work for the most part, but one thing is broken. the whole workflow seems to work fine, but the actual source code of the website itself is not updating properly, so the website ultimately does not get displayed. I need to dig into this deeper after a break.

6/9 - fixed it. everything works! http://multi-docker-env.eba-m6drmp8u.us-east-2.elasticbeanstalk.com/ (will probably take this down so i dont incur hosting costs). takes 2-4 minutes every time after pushing to main. I need to reassess current goals, and set a discrete goal for the month. 

Taking a moment to reassess and consolidate options: 
- Kubernetes scaling to finalize containerized deployments and keep learning CICD stuff.
- Go back to building web apps, and bring one of those through the current development workflow.
  - I wanted to redo a project management planning tool like trello, integrated with idea capture or something else to make it more useful for entrepreneurship planning.
  - Taskangel
  - Coinfind 
- Backend stuff, learning more Rust. The next thing wouldve been the rust/wasm game, but game feels off topic.
- Blockchain/cryptocurrency.
  - Ethereum protocol developer track
  - Dapp track (Alchemy or other courses)
I think ultimately i have to set goals one level higher. Personal goals for the year, for example. Whether that's a startup or getting a job or something. 

6/10 - initial goal would be to set up the deployment workflow for a NextJS app with postgres. I don't think redis is necessary. I need to plan out the site routing and figure out how the frontend/backend split would work for nginx. I think it's just one thing. Need to confirm. 
- Set up initial NextJS project to do a new trello clone; create-next-app, set up postgres and prisma, get auth setup.
- Once the baseline app is in a decent place, get docker workflow in place to dockerhub
- once dockerhub is updated, connect github actions to automate deployment.
- maybe just deploy to aws for completeness, even if it costs a little money. youll learn stuff about having something live in production from it.

6/11 - continue with basic app setup. auth setup focus next. didnt get much progress. low productivity day. 

6/12 - continue to set up auth. sign in/out working. there was an issue with `prisma generate`, but removing `output` folder `../generated` seems to have fixed it. i confirmed it's working directly with the postgres db running locally via docker desktop

OAuth Flow Overview: 
- NextJS app has a <form> that submits calling the action from NextAuth npm package that has the signIn/signOut functions on it.
- (Browser) Redirect user's Browser to Github servers including the client_id of the github_client_id, the app we set up in the github applications console. `http://github.com/login/oauth/authorize?client_id=123`. Github asks user if it's ok to share information with this app.
- (Browser) User says it's ok to share info with the app. 
- (Browser) Github sends a code back to our app to route `http://localhost:3000/api/auth/github/callback?code=456`.
- (App) App sends a follow up request to `http://github.com/login/oauth/access_token` including the clientId, clientSecret, and the `code` we got from github after authorizing
- If valid, Github will send an `access_token = abc123` back to our app
- (App) App sends another request including the access token to request info from Github about the user. `http://api.github.com/user` with authorization headers. Authorization: Bearer abc123
- Github sends back a json with the requested info, like name, image, email, etc.
- PrismaAdapter takes this info and stores it in our database. Create new User
- App creates a cookie and sends it to user's browser to authenticate them later automatically. NextAuth reads cookie data to identify authorized app user for future requests. 

6/13 - Thinking through all the pages on the site, and the data flow between each, and the overview of the whole application. Scope out the work needing to be done for a prototype. Core flow will be something like:  
  - Header in Layout across all pages. Sign Up/Sign In. 
  - Home Page also has link to Browse Top Projects (/projects, Show-Many-Projects-Page) or Create New Project (/project/new which will then create a /project/myProjectName)
    - Featured projects
    - Featured tasks
  - On /project/myProjectName (Show-Single-Project-Page), have:
    - /project/myProjectName/overview; "description of project" created at initialization
    - /project/myProjectName/board; trello board style
      - "inbox" pool of ideas
      - "tasked" (initial task submitted), "available task", "bounty outstanding until date" (1+ bounty hunters assigned), bounty completed, completion verified.
    - /project/myProjectName/tasks
  - On /tasks (Show all tasks page), have a separate user flow to view created tasks and give logged in users the option to make offers on the task.
    - Users create Tasks as part of the planning/organization flow. These can be rough ideas that arent fully formed, but require a description of the task needing completion, rough timeline, and a two part request bounty: one administrative fee, one task bounty prize.
      - Create Card. Push it through project to Tasks, attaching info/funds along the way.
    - Administrators consume/claim the adminstrative fee and formalize the process to be turned into a vetted task bounty. This administrator is responsible for seeing this bounty is completed and accepted. If this bounty times out, the administrator does not get paid, and possibly penalized. 
    - Bounty hunters view the task bounty board and can either "claim exclusive" putting their reputation on the line, or make a claim offer with more specific counter-proposals or details.
      - Bounty hunters then complete the task, and submit it for acceptance by the administrator, who in turn will need final acceptance from the task creator client. 

Additional issues that are a little bigger in scope to keep in mind: 
- If taskangel is going to become the core task management function (initialization, refinement, publication, claim, fulfillment), this should stand alone and be composable into other stuff systematically.
  - This would require thinking through the 'user' object and the data associations to the 'user' table; consider whether this should be in-db or on-chain.
  - Rethink whether "task" requires the trello-style project management component, or if that's out of scope too. but for now, it'll stay until proven extraneous. 
- Additional functionality is so easy to dream up, but hard to defer to a reasonable future time;
  - once the core task mechanism works, expand it to DAO orgs; improvement proposal proposal/discussion/selection flow
  - poap style initiatives to users; participation incentives for engagement or sponsored tasks? 
  - introduce a token to natively pay for task flow
  - list token so people can get paid and use it in daily life
  - add a project wiki to contain org entity knowledge
- Would be an interesting way to revive 'dead' projects by having the original team load up any remaining treasury tokens into a dedicated decentralized treasury accessible via hitting milestones. let the community self organize and push projects

Priority questions: 
- Does it make sense to dockerize the workflow onto docker hub, automate the ci/cd, then deploy before implementing the app specifics first?
  - The next step before implementing the app would be to get the docker workflow set up first. Need to look into dockerizing the nextjs project then getting the 'build' to run from the cloud.
  - Dockerfile.dev copy over package.json, run `npm install` then create volumes to map our local development folders to the container's `/app` folder. Probably want to simplify the setup with docker-compose so the docker run command doesnt have to be super complicated.
  - Eventually, for production, will need to swap out the dev server with a production web server, prob using nginx. Use a multi-step build Dockerfile; first a 'builder' phase to use alpine to build the project, then a second 'run' phase to use nginx as a BASE to run the nginx server using the built application.
- Does NextJS application count as a "simple static site" in regards to nginx's setup?
  - For production, https://thoughtrealm.medium.com/deploying-a-next-js-app-with-nginx-using-docker-ca6a5bbb902e has a walkthrough of setting up dockerized nextjs using nginx and prisma (mongo instead of postgres).
  - For development, just use the simple Dockerfile.dev setup using

`Dockerfile.dev` for development. This worked for react project, but needs to be adapted for NextJS specifically. 
```Dockerfile
FROM: node:lts-alpine
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
CMD["npm", "run", "start"]
```
`docker-compose.yml` for development 
```yml
version '3'
services:
  organize-app:
    build: context: .
    dockerfile: Dockerfile.dev
  ports:
    - "3000:3000"
  volumes:
    - /app/node_modules
    - .:/app
```

`Dockerfile` for production. 
```Dockerfile
# using staged builds
FROM node:18-buster as builder
# make the directory where the project files will be stored
RUN mkdir -p /usr/src/next-nginx
# set it as the working directory so that we don't need to keep referencing it
WORKDIR /usr/src/next-nginx
# Copy the package.json file
COPY package.json package.json
# install project dependencies
RUN npm install
# copy project files 
# make sure to set up .dockerignore to copy only necessary files
COPY . .
# run the build command which will build and export html files
RUN npx prisma db seed && npm run build

# bundle static assets with nginx
FROM nginx:1.21.0-alpine as production
ENV NODE_ENV production
# remove existing files from nginx directory
RUN rm -rf /usr/share/nginx/html/*
# copy built assets from 'builder' stage
COPY --from=builder /usr/src/next-nginx/out /usr/share/nginx/html
# add nginx config
COPY nginx.conf /etc/nginx/conf.d/default.conf
# expose port 80 for nginx
EXPOSE 80
# start nginx
CMD ["nginx", "-g", "daemon off;"]
```
`docker-compose.yml`
```yml
version: "3.9"

services:
  # this service should use the web image after you build it
  web:
    image: next-nginx:dev
    ports:
      - "3000:80"
    environment:
      NODE_ENV: development
  # this service is the database service using mongo from docker hub
  mongo:
    image: mongo-replica:latest
    restart: always
    ports:
      - "27027:27017"
    environment:
      MONGO_INITDB_ROOT_USERNAME: root
      MONGO_INITDB_ROOT_PASSWORD: password
```

6/14 - Thinking about creating 'project' first. Anyone should be able to create a new project. Projects should be stored in db. 

- Project is the highest level datastructure
  - Each project has many tasks, which are the atomic unit of work.
    - Each task should have: req task_id, req task_creator (user), opt task_tags (tag), opt comments (comment)
    - Each task can be 'tagged', which will allow for filtering by task. default tags "new" and "unassigned", maybe "unconfirmed/unvetted" 
    - Each task can have many 'comments' on it to discuss work.
    - Each task can have a 'user' assigned to complete the task. 

Thought about "initiatives" field, but it should come later and be an optional field. Each project could later contain "initiatives" which are groupings of tasks that are associated with a specific goal; ideally a specific measurable outcome by a specific date. Dont need this yet though.
This could go the other way too, instead of trying to group above a single task, it could have a 'subtask' or maybe groupings of tasks together, which can maybe be called a "work-order", which makes sense to assign to a single user to be responsible for as a grouping. No Boards, No Initiatives yet.

Let's get the basic stuff done, then let user behavior and user research drive improvements. get basic simple tasks implemented first.

6/15 - Goal is to implement Project and Task next. 

6/16 - Look into Drag and Drop functionality. Leading library is https://docs.dndkit.com/

Auth.js note: using auth() dynamically accesses the cookies. But useSession makes a backend call to check auth status. 

6/17 - got project creation mostly done, but now im rethinking what needs to happen in the UX flow. users dont just randomly create projects and tasks. i need to think of a better flow for creating tasks. why do people create tasks, what happens to tasks when theyre created in the app, what are we expecting people to do with new tasks once created. who sees newborn tasks, and what is the next step we want to get them to? 

6/18 - ideally next would be task-planning-flow. Who creates Projects? Can we assume projects are created? Are tasks associated with projects always? Who can create new tasks in a project? Do we need an 'admin' whitelist? Once a task is created, what's expected to happen to the new task? How is a task 'finished' exactly, what comprises a completed task. What are all the paths to get there from newborn task? 

I have to clarify what exactly im building. Several ideas seem to be clouding together. 

1. The idea of a personal-organizer, which is basically just a kanban board
2. Bountifying a task from within the organization workflow. Task > add money > broadcast. 
3. Administrative assistance for organizing and clarifying projects. (Human/AI).

I guess the use case I want is: 
- Have idea for new project
- Enter as much detail as i have about the project
  - Can be handled by AI or as a task for a freelance project/product manager to take over work on. 
  - Goal: Output a project management plan aligned with goals
- Distill into specific tasks
  - Enable bounty on tasks to get people to start working on it
- Update plan as it progresses

Step 1: Create Project 
- Title
- Describe your project
- Set objective
- Success metric. How it's measured. Who measures it. 

6/21 - Have been working in the TaskAngel repo. Spent a day or two better thinking through the UX of the site and how I want it to work exactly. Conducted user research and made a few wireframes and UX flows, separating out Owner flow and Admin flow. Owner just creates the idea, pays for it, and approves it along. Admin flow isnt built yet, but it would receive the initial prompt and structure it first, then act as a project manager taking responsibility for pushing it through to completion, using individual "tasks" as steps forward. Did form validation using zod. 

6/22 - Decided to add a "Balance" field to "Projects" and finish the project creation flow then read/display from db. Didnt get much done (Sunday). 
6/23 - Goal is to get the project creation into db, then refactor to add Balance to User. 

project creation done, added balance to User, but typescript schema won't pick it up. I have to find a way to extend the DefaultSession type. getting error `Property 'userBalance' does not exist on type 'User'.ts(2339)`. It appears on the object and i can access it, but the type definitions dont like it, so keep erroring. 

6/24 - figured it out with the help of kapa bot in nextjs discord. 

Prisma updates its types, but NextAuth's session type must be manually extended to reflect new fields on session.user. This is not handled by prisma generate or prisma migrate alone.

> When you add a new field to the User model in your Prisma schema and run prisma generate and prisma migrate, Prisma will update its generated types for the database models. However, the session.user object provided by NextAuth.js does not automatically include custom fields you add to your Prisma User model. This is why your linter does not recognize the new field on session.user.
> 
> To fix this, you need to extend the TypeScript types for the NextAuth Session object to include your new field. This is a common step when customizing the session shape in Next.js apps using NextAuth and Prisma.
```ts
   // next-auth.d.ts
   import NextAuth from "next-auth";

   declare module "next-auth" {
     interface Session {
       user: {
         // default fields
         name?: string | null;
         email?: string | null;
         image?: string | null;
         // your custom field
         newField?: string; // adjust type as needed
       };
     }
   }
   
```

6/25 - didnt get much done today. 
- next thing to do is figure out how to handle description during project creation. I think the flow would be to run it through an ai workflow to parse the initial message and turn it into a set of tasks. to do that i need the ability to have tasks, unless i want just a list. 
- ability to create tasks
- description in, list of initial tasks out.
  - deduct some balance to do this.
    - need ability to modify balance (add to balance).
  - allow modification loop.
  - "submit initial task list"
- once owner is satisfied with initial task list, have 'administrator' join to manually look through it, suggest improvements, and give recommendations.
  

6/26 - Task creation implemented, but balance calculations arent done yet, and the flow from project submission to initial task list creation isnt defined yet. Think through the workflow; exactly what's expected to happen after project creation submission? how does it yield a task list for approval?

6/27 - got tasks rendering. minor issues like wanting 'elapsed time' since creation or last updatedAt. would need to build a whole function for it. do this later.

6/28 - project createable, tasks createable, comments are alright. next would be to really work on the workflow. on project submission, pass the 'description' through an ai workflow to return the initial taskList, and build out a dashboard or interface where projectOwners can interact with the initialDraftTaskList to approve it, and attach funds to entice projectAdministrators. 

Objective for the day: get n8n running on docker and get the create-project form submission to trigger an n8n webhook-trigger. 
- (success) Fill out form. submit.
- (success) n8n webhook trigger
  - (work in progress) work on prompt
- (success) return value in a specified format that can be easily turned into 'task' items.
- (success. decision made, it's out of scope, do it later) decide if i want to return format in a useful 'itinerary' or 'initiative' or something that gives an overview of the proposed project. "project proposal". this *is* the project so just return in the project.
- figure out how to programmatically create tasks from the webhook return
- render to owner.
  - would be cool to nest tasks based on dependency, so you only see a collapsed list of all the stuff that can be worked on right now, and everything behind an unfinished dependency is hidden.
- owner assesses proposal
  - approves proposal, depositing funds.
  - sends it back for administrative opinion and proposal, with the ability to comment. 
    - goes to 'proposal request' bank where admins can see the initial proposal, and any notes the owner had. 

notes: initially using sqlite on n8n. will migrate to postgres later before deploying.

example output for prompt `create music for my game about futuristic space exploration` 
```json
{
  "tasks": [
    {
      "taskTitle": "Define Game Music Style",
      "description": "Research and decide on the specific style and genre of music that aligns with the futuristic space exploration theme.",
      "deliverable": "A written document outlining the chosen music style and genre, including references or examples.",
      "acceptanceCriteria": "Document is clear, well-researched, and aligns with the game's theme.",
      "dependencies": "None"
    },
    {
      "taskTitle": "Create Music Mood Board",
      "description": "Compile a mood board with audio clips, images, and descriptions that reflect the desired emotional tone for the game music.",
      "deliverable": "A visual mood board that includes at least 5 audio samples and relevant thematic images.",
      "acceptanceCriteria": "Mood board is visually appealing, coherent with the chosen music style, and provides an emotional direction.",
      "dependencies": "None"
    },
    {
      "taskTitle": "Compose Main Theme",
      "description": "Compose the main theme music for the game, utilizing the defined music style and the mood board for inspiration.",
      "deliverable": "An original music track of at least 2 minutes in length, representing the main theme.",
      "acceptanceCriteria": "The track is original, fitting within the specified style and mood, and is of high audio quality.",
      "dependencies": "Define Game Music Style, Create Music Mood Board"
    },
    {
      "taskTitle": "Create Background Music Tracks",
      "description": "Compose a series of background music tracks that can be used throughout various game levels, maintaining consistency with the main theme.",
      "deliverable": "Three original music tracks, each 1-2 minutes in length, suitable for looping.",
      "acceptanceCriteria": "All tracks are original, cohesive with the main theme, and fit within the defined style.",
      "dependencies": "Compose Main Theme"
    },
    {
      "taskTitle": "Develop Sound Effects",
      "description": "Create custom sound effects to enhance the game experience, including effects for actions like jumping, collecting items, and interactions.",
      "deliverable": "A collection of at least 10 original sound effects in high-quality audio format.",
      "acceptanceCriteria": "All sound effects are original, varied, and enhance the gameplay experience as intended.",
      "dependencies": "None"
    },
    {
      "taskTitle": "Mix and Master Music Tracks",
      "description": "Mix and master all composed tracks to ensure they are polished and ready for integration into the game.",
      "deliverable": "Final versions of all music tracks, expertly mixed and mastered.",
      "acceptanceCriteria": "Tracks are balanced, professional-quality audio that meets industry standards.",
      "dependencies": "Compose Main Theme, Create Background Music Tracks"
    },
    {
      "taskTitle": "Collaborate with Game Developers for Integration",
      "description": "Work with developers to integrate the music and sound effects into the game engines, ensuring synchronization with gameplay.",
      "deliverable": "Confirmation of music and sound effects successfully integrated into the game.",
      "acceptanceCriteria": "All audio components are properly integrated and function as intended within the game environment.",
      "dependencies": "Mix and Master Music Tracks, Develop Sound Effects"
    }
  ]
}
```
6/30 - look up how to bind these results to actionState or otherwise get it to the ProjectShowPage
> To trigger both a client-side function (like calling a third-party API in handleSubmit) and a server action with the same button click in Next.js, you have a couple of options, but there are some important constraints:
> 
> Forms with Server Actions:
> When you use a form with an action prop set to a server action, the form submission will automatically call the server action and pass the FormData. If you want to do something on the client (like call a third-party API) before the server action, you need to intercept the submit event, perform your client-side logic, and then trigger the server action.
> 
> Passing Data from Client to Server Action:
You cannot directly pass arbitrary JavaScript objects (like your "result" from a third-party API) to a server action via a form submission, because only form fields (FormData) are sent. If you want to send the result to the server action, you need to serialize it and include it in a hidden input field or submit it via a custom fetch call.
> 
> Example: Client-side Logic + Server Action
```tsx
'use client'

import { useRef } from 'react'
import { myServerAction } from './actions'

export default function MyForm() {
  const formRef = useRef<HTMLFormElement>(null)

  const handleSubmit = async (e: React.FormEvent<HTMLFormElement>) => {
    e.preventDefault()
    // 1. Call third-party API
    const result = await callThirdPartyApi()
    // 2. Set result in a hidden input
    if (formRef.current) {
      const input = formRef.current.querySelector('input[name="apiResult"]')
      if (input) input.value = JSON.stringify(result)
      // 3. Submit the form to trigger the server action
      formRef.current.requestSubmit()
    }
  }
return (
    <form ref={formRef} action={myServerAction} onSubmit={handleSubmit}>
      {/* other form fields */}
      <input type="hidden" name="apiResult" />
      <button type="submit">Submit</button>
    </form>
  )
}
On the server:
ts
'use server'

export async function myServerAction(formData: FormData) {
  const apiResult = formData.get('apiResult')
  // Parse and use apiResult as needed
}
```

> Key Points:
> You must serialize the result (e.g., as JSON) and include it in the form data.
> The server action will only receive data that is part of the form submission (i.e., in FormData) see: How to create forms with Server Actions.
> If you want to pass the result to the next page, you can redirect in the server action and pass data via URL params, or store it in a database/session and fetch it on the next page see: Mutations with Server Actions.
> 
> If you need to do more complex client-server coordination, you may need to handle the entire flow on the client and call the server action via fetch, but this is less idiomatic in the Next.js App Router model.
> 
> For more advanced state passing between pages, consider using a database, session, or other persistent storage, as you cannot directly pass large objects between client and server actions except via form fields or API calls.

Creating all the tasks on the tasklist. 
> To store the value of "tasks" (an array of task objects) in a "tasks" table using Prisma, you would typically use the Prisma Client's createMany method after you have created the project and received the tasks from the third-party API. Here’s how you can structure this in your server action, based on the patterns shown in the knowledge sources:

> Create the project using Prisma.
> Call the third-party API with the project description.
> Store the returned tasks in the database, associating them with the created project.

Example that demonstrates these steps:

```tsx
'use server'

import prisma from '@/lib/prisma'

// ... (validation and project creation code above)

const project = await prisma.project.create({
  data: {
    name: validated.data.name,
    description: validated.data.description,
    // ...other fields
  },
})

// Call the third-party API with the description
const response = await fetch('<https://third-party-api.com/process',> {
  method: 'POST',
  body: JSON.stringify({ description: validated.data.description }),
  headers: { 'Content-Type': 'application/json' },
})
const { tasks } = await response.json() // tasks: [{ title: string, ... }, ...]

// Store tasks in the database, associating them with the project
if (Array.isArray(tasks) && tasks.length > 0) {
  await prisma.task.createMany({
    data: tasks.map(task => ({
      title: task.title,
      // ...map other task fields as needed
      projectId: project.id, // assuming a relation exists
    })),
  })
}
```

> Notes:
> This assumes your Prisma schema has a Task model with a projectId field that relates each task to a project.
> The createMany method efficiently inserts multiple records at once.
> You should adjust the mapping in tasks.map(...) to match your actual task object structure and your Prisma schema.

Heck yeah! I got the tasks to populate on the ProjectShowPage after being written into the Tasks table in postgres. Solid progress!

## July 2025
June was a pretty productive month. I'm preparing to move back to Seoul, and I've started to tell people about this project, with strong feedback so far which has been encouraging. I'm finding that I am learning a lot, but new features really challenge my understanding of how things work. I have been trying to keep the codebase clean, but now I better understand how much goes into a refactor. For now, the priority is getting things working without making too big of a mess. I am also finding how the hardest part is to clearly define the user flow and dataflow. The site is made, it's dockerized, and things are working well. The "project owner" workflow is pretty much finished. Next is the "admin" workflow and the "bounty hunter" workflow. 

7/1 - Consider adding a "approvedByOwner" and "approvedByAdmin" boolean flag to the initial taskList, and/or to each individual task - when both approve, the task is set. Admin flow should be to start on the homepage, browse potential projects to admin on, see their current admin tasks. "current" and "browse new" projects. Admins need more of an interactive dashboard to manage things and do work. 

Setting role-based permissions on the page so only the owner and the authorized/selected administrator has access: https://authjs.dev/guides/role-based-access-control

Maybe use a data-access-layer to restrict access to pages/actions. https://nextjs.org/docs/app/guides/authentication#authorization

I think for what i need, it'll be sufficient to add more fields to each "Project" in the db to store the "owner" and "admin", and put in a server action that allows the admin to approve adding an admin. 

Initial feedback on the "project owner" user flow uncovered some frictions. 
- Fiverr and upwork dont require users to commit anything in the initial stages of discussing the project. they just chat with potential people and then choose to hire them or not.
  - Does an "admin" work bond have enough value to warrant project owners escrowing funds up front if the admins fail? What would this look like? PO creates project with initial deposit of 100 credits. Administrator says they can do it for 120credits, and offers a 120credit bond themself to 'put money where their mouth is' to ensure they can complete the spec for that budget.
  - There needs to be a way to ensure people dont get screwed from every angle; owners submitting, admins doing some initial work. Maybe it's to be expected and the platform should just bear the risk and rate limit some other way.
  - Maybe the place to add more friction is onboarding administrators, and having a vetted set of admins would open up a lot more possibilities for how much trust we can give the admins instead of some random freelancer. Vetted freelancer with credentials? 

7/2 - lets get the initial version done then revisit the UX. more user research is needed for that anyway and it doesnt change the fact that a working prototype will proabbly help overall. get it working and push it to live first woth the basic suboptimal user flow and itllbe easier to reassess the whole flow. 
- claim, do, get paid. 
- PO submits project. it can either get broken up into tasks and then broadcast out for individual workers to claim or PO can choose to attach a manager into the tasklist. attaching a manager could be a separate flow where discussion happens and a budget and deliverables and stuff are contracted ahead of time and a project deposit is made. 
  - for direct-to-bounty tasks, PO would have to attach a deposit on the task itself. the task would then go on the bounty board and be a self contained unit of work that is paid upon. 
  - completion of the individual step. two public bounty versions: (1) race to completion and (2) exclusive work hold, where worker claims a task and attaches a stake (reputation or money) to promise task completion. 

7/3 - got user feedback and demoed to someone in crypto. bounty concept works a lot smoother in crypto and ai is seen with a little skepticism and commoditization but it went ofer decently well. main feedback is that there is a concer over whether thr platform cns really deliver on its promise to actually solve my prohlem and deliver a compete and safisfactory solution. crypto also has seen some trouble with oracles and deciding the final status of results (polymarket and dao votes) so crypto would want stronger validation of results. 

7/4 and 7/5 - didnt code much. went to seoul for baseball game. 

7/6 - running into issues rerunning n8n. lost login info. Next steps would be to focus on the admin and worker experience and flow. 
- Lead generation (email, upwork, linkedin, in-person, etc) 
- Sales meeting
- Kickoff meeting
- Project delivery; check ins
- Retention follow up

7/7 and 7/8 - completely lost these days. 

7/9 - goal: either get the ownerApprove and adminApprove implemented or switch gears and work on something else. Feeling stuck and unproductive on this. motivation lacking. pretty disheartened by things not going my way. 

7/10 - it's concerning how my focus has been completely lost. it's disheartening when i think about the project. is it because i lack clarity on what to implement next, or because showing the prototype in development to a few people gave me enough of a dopamine hit to make this project feel complete, when it's clearly not complete yet. 

7/11 - the past turns out to be a week was off the rails. im going to give myself the weekend to resync, not feel guilty, then get ready to come back on monday. 

7/12 - this is fine.

7/13 - started bleh. but started to re-expose to the codebase. easing back in

7/14 - lets give it a restart. Going to map out the current project. Getting back into it will prob be easier when it's a lot clearer the exact next steps needed. 

In the future, when having a brainfoggy day, prob a good diea to block out a set amount of time, and just stay on-topic for that amount of time, even if it's 10 minutes, or 1 hour, or 4 hours. Forcing myself to "be at work" might help instead of wasting that time on something completely unrelated.

Back to fundamentals. 
Reviewing Prisma and how the schema is set up, to get a more intuitive sense of how things are working. 

When creating relationships in a relational db setting, need to define whether it's one-many, many-many. Users and Posts would be a one-many relationship. 

```prisma
model User {
  id Int @id @default(autoincrement())
  posts Post[] //this field only exists as a relation to Post, and is not a field in the db.
}
model Post {
  id Int @id @default(autoincrement())
  author User @relation(fields: [authorId] references: [id]) //this relates the authorId field with the "id" field of the User table. also does not exist as an accessible field in the db. 
  authorId Int

  title String //the rest of the stuff unrelated to the relationship
}
```
7/15 - reviewed prisma write. not very productive

7/16 - Setting a timer for 25 mins got me to work on it for an hour and made solid progress. Maybe the key to this is deciding to give it a shot, removing distractions, and giving it a go for 10 mins. 
gave advice on startup project selling ai to law firms. selling simple things is a skill too. 

7/17 - did more user testing and got some good feedback. the flow makes sense, and the admin-as-value made sense. they also initially thought of bypassing admins to diy, but seemed to understand the admins are the value.

7/18, 7/19 - no progress. prepping for moving for the next few days. Move progressing well
7/20 moving prep. 
7/22 got advice that the project might be aiming too small and it would work. better for raising to go bigger. i think im fine with how its going now until im sure the problem is being solved. 

7/23 i think i need to figure out whats happening with my focus and motivation. its just completely falling by the wayside and not even popping into my brain that i need to be working on this. is this adhd, or some sort of blindness? is it a lack of motivation or something with dopamine? does the task feel marked as completed mentally because i made it to a small milestone? how can i restart this to reignite focus? this is unsustainable and a waste of time if i dont seize the opportunity. 
7/24 this doesn't help. just makes me feel bad about losing all this time
7/25 wow time flies. got ac cleaning and washing machine cleaning and some shopping. will pick up plants tomorrow. 
7/26 went to code meetup but it was not that productive. ended up taking more about startups than code. 
7/27 going to visit new sunday meetup 


