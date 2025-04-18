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
