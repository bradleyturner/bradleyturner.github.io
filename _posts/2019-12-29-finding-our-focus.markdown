---
layout: post
title: "Turning an open ended problem statement into small shippable improvements"
date: 2019-12-24 20:19:12 -0400
categories: jekyll update
excerpt: "I worked on improving our new user experience by conducting research, exploring and testing concepts, and breaking them down into individual problems we could solve"
image: "focus.png"
---
In the fall of 2019 the product team identified the new user experience as an area of opportunity for us to work on. I dug deeper to understand the current challenges and areas for improvement, digging into current usage data, conducting a UX audit, and running concept testing to focus our efforts and outline proposed phasing to tackle various areas for improvements.

We are still actively working on testing these new features and initial results should be coming soon!

## We knew we had a student retention problem.

At Handshake, our mission is to enable all students to build meaningful careers by helping them find their next steps.

We do that by providing a personalized experience that helps students navigate all the job postings, employers, events, resources, and information they need without depending on a personal network.

In order for us to do those things, students need to use our product during their career search. **Unfortunately, students weren’t engaging with Handshake in the ways we need to help them effectively.**

![Pie graphs showing 75% of students didn’t return within 7 days of signing up and 50% of students didn’t return within 30 days of signing up](/assets/images/finding-our-focus/intro-stats.png){:class="pop-out-width"}


## I conducted an audit of the current experience to identify areas of opportunity

Before jumping to exploring solutions, I wanted to understand what the experience was like today that might be causing these poor retention rates.

I documented the current experience, evaluating it through the lens of UX best practices, and partnered with our data scientist to identify how the current flow was performing at scale. I documented the flow in a Google Slides deck and shared it out with the team.

![Presentation screenshot](/assets/images/finding-our-focus/nux-audit.png){:class="pop-out-width"}

**I started the deck with an overview of the current flow, which looked like this:**
* Agree to terms of service
* Pick privacy status
* Go through 10 question on boarding flow
* Land in the product on the initial page you were trying to get to when you had to sign up (For 75% of users that page was the home page)
* Home page has a few actions to take in the top banner
* Email drip campaign – 1 day, 3 days, and 7 days after agreeing to terms of service

**General drop-off**
* 1 in 5 students don’t make it past on boarding
* Only 75% of students who finish on boarding are directed to the home page
* 15% of students don’t take any action on their first day after landing on home for the first time
* Only 40% of students who make it past on boarding see a job page on their first day

### In onboarding we were trying to communicate 3 core value props in between asking 10+ questions
As I was evaluating the experience, I realized that we were trying to pitch 3 different value props to students without showing them any real content, asking them 10+ questions along the way.

The value props we were pitching included:
* Provide more relevant job recommendations by asking questions about their career interests
* Get students noticed by employers by encouraging them to make their profile public and asking questions about their experience and qualifications
* Build the peer to peer community by prompting students to make their profile public

Pitching these 3 value props and asking all of these questions was causing 1 in 5 students to leave the product before they got to see any of our content. Digging deeper, we found **onboarding drop-off is highly correlated with low retention and applicant rates.** Students who complete or skip on boarding are 35% more likely to come back and 2x likely to eventually apply to a job than those who drop off

Fixing this onboarding flow could have a large positive impact on retention and applicant rates.

### First day traffic was all over the place, suggesting lack of focus for students
For students who did make it through our onboarding flow, we found that their experience wasn't very directed. 

We found that 15% of students didn’t do anything after landing on home. The most popular page to visit is postings at 40%, with profile at 37%, notifications at 25%, and jobs at 22%. This was a result of the home page having prompts to fill out your profile with almost equal weight to exploring jobs.

We found that **students who visit job search or view a job on their first day are 2-3x more likely to end up applying**. We could optimize the home page to better direct students to find relevant jobs on their first day.

## If we were going to make improvements here, we'd need to separate out these 3 value props
One of the biggest problems I wanted to solve was cramming all 3 value props and asking for information before we were able to show students anything valuable in return.

I wondered if we could spread them out over the student’s journey, starting with the promises we could deliver on fastest. I explored concepts that introduced the value props in the order:
1. **We will help you find relevant opportunities.** We know a majority of students come to Handshake to look for jobs. If they don’t see jobs they are looking for on their first experience, why would they come back? Let’s get those jobs in front of them and start showing them that we can deliver on what they are looking for.
2. **Employers will proactively reach out to you when you fill out your profile.** This requires a good amount of effort on the student’s part to fill out their profile so they will be noticed by employers. Let’s introduce this concept after they’ve seen all of the job opportunities that we have for them. That will make them more likely to want to fill out their profiles so they can get those jobs.
3. **You can message your peers about career-related questions when you make your profile public.** Let’s introduce this when students have found jobs or employers that they want to learn more about instead of introducing it out of context.

For my first concept, I tried shortening the onboarding survey to just questions that result in more relevant job recommendations and moved the other prompts later in the flow:

![Wireflow of an experience showing a shortened onboarding experience](/assets/images/finding-our-focus/shortened-survey.png){:class="pop-out-width"}

For my next concept, I made the initial job relevance survey optional, encouraging students to fill it out with a prompt on their homepage, but not blocking their experience:

![Wireflow of an experience showing an opt-in onboarding survey](/assets/images/finding-our-focus/opt-in-survey.png){:class="pop-out-width"}

As I was exploring the shortened onboarding concepts I realized the questions we were asking were duplicative of search filters students would later use when searching for jobs. The third concept explored removing those questions entirely and trying to use their search inputs to tune our recommendations instead of explicitly asking.

![Wireflow of an exploratory experience that learns your interests as you interact with the product](/assets/images/finding-our-focus/incorporate-survey-into-normal-flow.png){:class="pop-out-width"}

We reviewed these 3 concepts with product and design team leads, generating a list of assumptions we wanted to test before committing to any one direction.

1. If we remove onboarding and personalize the experience over time, will students perceive Handshake as more or less relevant?
2. If we embed the value props throughout the student experience will they still understand all 3?
3. Would students be surprised or confused by not having an explicit onboarding process?


## We tested 2 concepts to allow students to compare their experiences
We recruited 6 students from various schools and majors across the country who had previously signed up with Handshake, but not interacted much with the product. I led remote user testing sessions with these students, starting with understanding their previous experience searching for jobs and then having them click through 2 prototypes, digging into their experience as they went.

![Presentation screenshot](/assets/images/finding-our-focus/prototype.gif){:class="pop-out-width shadow add-margin"}

One prototype had a shortened on boarding experience that asked students their job preferences before showing them the product. The other dropped them right into the product with the ability to explore in whatever way they saw fit. We alternated which prototype we showed them first so that we didn’t bias their experience by always starting with one version.

### We felt confident moving forward with a version that didn’t include onboarding
Overall the version without the on boarding survey had better results. Students were still able to quickly find relevant jobs through prompts when we didn’t ask them up front and they didn’t get stuck on questions they didn’t know the answer to like what job roles they were interested in.

By having an explicit prompt around getting proactive messages from recruiters by filling out your profile we found that students didn’t previously realize that was possible, and students still encountered community features throughout their experience. There was only one student who specifically mentioned that they were surprised by not having an introduction before getting dropped into the product.

While we weren’t explicitly testing the layout of the home page, we heard from many students that they felt overwhelmed by all of the different types of content we presented them with. This would be top of mind as we continued iterating on this project.

## We needed to break this down into smaller shippable pieces
We felt confident about moving in a direction that introduced value props throughout the student experience and allowed students to more easily find the type of content they were looking for.

We refined this direction and presented a prototype to the iOS and web engineering teams, discussing how we might separate the work into deliverable pieces. We decided to tackle the pieces like this:

![Phasing visualization](/assets/images/finding-our-focus/phasing.png){:class="full-width add-margin"}

1. **Content type navigation** – surface the core types of content in a digestible manner at the top of the home page, allowing students to pick their path if they know what they are looking for
2. **Job role exploration** – for students who don’t know what they are looking for, start to surface career paths they might be interested in
3. **Home page prompts** – start to set us up to introduce the concept of getting proactive messages from employers by building out our first home page prompt
4. **Global search** – condense the various content type searches into one search experience with shared UI patterns

With this phasing we are able to start supporting all of the experiences we will need to eventually remove the onboarding survey entirely. This way we can test all of these experiences individually without waiting until we have built everything out all at once.

## Nailing the UI for content type exploration was a team affair
While exploring UI options for these 6 cards at the top of the page, I ended up collaborating with 3 other members of the design team, each of us contributing directions and evaluating options.

Overall we tried hundreds of options, playing with size, color, shape, imagery, you name it. 

![UI explorations](/assets/images/finding-our-focus/card-explorations.png){:class="full-width add-margin"}

We were also starting to incorporate a new brand direction into the product and this was the first project to test out some of those ideas.

In the end, we wanted something that made a statement the first time you saw it, differentiating us from other job search platforms students might be using. We also wanted to make sure the content types were clear and were the focus of your attention when you landed on the home page.

Because of these reasons, we opted for a simple card with the content title, a short descriptions, and a supporting spot illustration that didn't distract from the actual title. We set these cards on a deep blue background to draw attention to them without making the UI feel overwhelming.

![Home specs](/assets/images/finding-our-focus/final-ui.png){:class="pop-out-width add-margin shadow"}

Heading in this direction also resulted in needing to tune up the styling of the main navigation bar to allow the content type navigation on the home page to stand out.

After we found a direction we thought was most successful, I spec’d out the UI details to make it easier for the engineering team to implement the new styles we were introducing and fine-tune the responsive behavior.

![Home specs](/assets/images/finding-our-focus/home-specs.png){:class="full-width add-margin"}

![Navigation specs](/assets/images/finding-our-focus/nav-specs.png){:class="full-width add-margin"}

Reflection:
Since this project included so much conceptual work and tons of UI exploration, engineers found it challenging to understand what was ready to be built and shipped and what was still in flight. As a result of this confusion I put together a Figma file template for our team that breaks the pages into sections that align with the phases of our design process.

## We are improving the experience one piece at a time
The first phase of this project – the content type navigation – is now being A/B tested to understand how it impacts first day traffic, retention rate, and eventual application rates.

I’m now working on the next pieces of the project which will continue to address our areas of opportunity for the new user experience, heading in a direction which will allow us to remove friction and embed our value in contextual areas throughout the student experience.
