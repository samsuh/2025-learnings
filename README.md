# 2025-learnings

## Purpose
The purpose of this file is to track and measure the different topics and levels of learning accomplished over the year. Additionally it is a scratchpad and workspace for me to aggregate the different resources I found useful and that I want to revisit at a later date. 

Watching someone build a qc at home using lasers:
https://youtu.be/muoIG732fQA?si=iLFFr_RIAuqDQVb4
Thoughts: illustrates basic qc application using light and a prism. 

Quantum Computing Basics video
https://youtu.be/tsbCSkvHhMo?si=AyzbY2ubXUhdMgrG
Started on Jan 28, 2025
Completed Jan 31, 2025 
Thoughts: It was a very well made course to introduce the various concepts in QC. I realized that I need better fundamentals in Linear Algebra. 

Linear Algebra Fundamentals 
https://youtu.be/rSjt1E9WHaQ?si=N6Us_fWzsGPYv6ph
Started on Jan 31, 2025 
Completed: Not Yet. 
This one did not work for me. I found a different Linear Algenbra tutorial to follow. 
Working through https://youtu.be/3Bf9oh7nkus?si=dG5tszsEYr0atskT (Korean guy with english voiceover) 

NextJS course on Udemy
https://www.udemy.com/course/next-js-the-complete-developers-guide/
Completed it last year, but going through it again with a better understanding of SQL and databases. The goal here is to get practice with the NextJS side but also to understand what exactly is happening on the database side. 
Thoughts: It's already going well, with more of the prisma ORM stuff making more sense. 
Progress: 
Snippets Project 
A few days in after helping host the bootcamp, I'm getting into the second project in the tutorial and it's making sense. There are some changes since Next14 that require some refactoring/adjusting. implemented the routing and rendering to homepage of the list of snippets. i went through another iteration of spinning up the nextjs project. got through initial setup, prisma setup, create resource page, creating the resource on the db, getting and rendering a list of all resources, and showing individual resource on its own page. Next I have to focus on building out the Edit page and then delete - it's a client component because it wants to use the monaco editor which requires both state and hooks. remember to use legacy install for monaco because it broke with Next15 ```npm install @monaco-editor/react --legacy-peer-deps ``` client components should be separated out into the /components directory to make them both reusable and keep things organized. The edit page makes sense, but im having trouble thinking of it from scratch. the props comes into the function, create an interface for typescript to take in the params from the url and wrap it in a Promise because next15 changed that. once it's there, create a components folder at src/components and create the editor as a client component to use hooks/state. server components for data fetching, client components for working with it locally using state/hooks. I cant seem to get rid of a warning message about awaiting params.id, which should be taken care of, but it might be a bug in nextjs15. i'll leave it and proceed. Put server actions into an /src/actions/index.ts file to organize and reuse server actions. running the server action from inside a client component is pretty complicated; can still do it by (1) binding the state to the function call, (2) watch for changes (anything besides form submission like onClick) and use startTransition to directly call the action with the new data. startTransition will make sure to update the data before navigating away. edit works, but it's not automatic/intuitive yet for me, so i will practice that part. Practicing it helps, but had to break it down into discrete steps. Not sure if i would know all the steps intuitively. Was able to get through most of the CRUD, but stuttered a few times on the next15 Promise syntax for accessing props, and the formData bind functions when calling a server action using data outside of the formData being submitted as in the deleteSnippet functionality. Almost there. Styling needs to be worked on too, but is a lower priority. Added error handling for form submission using useActionState in NextJS 15, which replaces useFormState hook from react-dom. it makes sense. not sure if i can do it all rote from memory, but the concepts are all clear. caching concept also clear, and simple using ```revalidatePath('/')```. 

Reddit clone project 
Initial project setup: Install prisma, HeroUI (aka NextUI), and AuthJS (aka NextAuth). Perform initial setup. 
prisma schema setup including required schemas for auth flow 
heroui including setting up provider and picking it up from the next project
auth flow including setting up oauth credentials, callback route, and auth related server actions
