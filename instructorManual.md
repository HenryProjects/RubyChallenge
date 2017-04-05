Instructor Manual
====================

Put any content here that might be a good supplement for the instructor in their preparation for doing the course
## Preparation
  * Invite speakers for the afternoon sessions  
  * [Prepare AWS instances](instructor_aws_creation.md) for students (NOTE: You may want to wait until the end of the first day, to confirm attendence before creating the images).  
  
## Course Structure & Timing
   * Day 1
     * Introductions
     * Culture and Company
   * Day 2
     * Products 
     * Metrics to Events
     * Main project
   * Day 3 
     * New Relic Architecture (? TBD)
     * Main project continued  
   * Day 4 
     * CEO for the day -- Using Insights to solve business problems

## Introductions

Welcome them to the company, learn about their teams, talk about their backgrounds, wins, and fails.
Ask students why they came to New Relic. 

Draw the "3 circles and a smiley" architecture diagram on a whiteboard. As each participant identifies his/her team, add his/her name to the diagram in the appropriate place. 

Periodically re-inforce themes that come up. Usually, this is: company culture and people, great tools. 
These themes can be a lead in to the Goals and Values talk. The commonalities build the team mindset.  

**To Do**: Setup a section on the board with 'Unfamiliar Terms'. Every company has terms we've never heard before, New Relic is no exception. What are some ones that have or are tripping us up.

## Culture and Company 
### Goals & Values

Watch Lew's presentation of these materials:  
[New Relic's Vision, Goals and Values](https://newrelic.atlassian.net/wiki/display/VGMOM/*New+Relic%27s+Vision%2C+Goals+and+Values) - Video of Lew's Presentation of this topic from Project Hi-Five (2015-05)

If that doesn't load, feel free to use the slides and go through the slides yourself.

/projectFiles/2015 Project Hi-Five Slides/Goals_Values_4-15_FINAL.pptx

Slides: 2-4, 6-20

The engineering culture is continually evolving to allow people to be efficient, effective and not frustrated. The original engineering leadership team started with "What are the characteristics of the place we want to work? What do we not want in the place we work?". There is an emphasis on transparency and communication. Slogan: *"Have empathy; expect excellence."*

See if you can tie Goals and Values back in to parts of what we'll be doing in class throughout the week

### Office "Hacks"
The Portland office has several design elements that were deliberately built in to foster behaviors in line with our values. 
   * Pink noise to foster communication without disrupting others
   * Lunchroom to encourage connection during lunch. "No forks at the desk" 
   * Lights turn off at 6 to encourage team to respect personal time
   * Corners are "common area" for interaction. No corner offices to indicate hierarchy.

### Hiring Culture
In addition to being technically competent, New Relics must be able to interact as part of a team. Some call this "We don't hire assholes", others ask "Could I go on a roadtrip with this person?". The idea is that every person will need to interact with most of the rest of the team; people who cannot share well will make the team weaker over time. For techies, reference [Metcalfe's Law](https://en.wikipedia.org/wiki/Metcalfe%27s_law) on network design.

## Product Strategy
Use [Jim Gochee's Project Hi-5 Slides](projectFiles/2015 Project Hi-Five Slides/Jim_Gochee_CKO_4_15_FINAL.pptx) to introduce strategy and product. Skip Slides: 11, 19-30...these can trip you up if not put in context. 

## Day One Finale

Talk a bit about Lew's background, why he loves working here, and how we're making great products that solve real problems. "Tease" the fact that tomorrow will be deeper investigation of the products. 


## Products
Start by revisiting [Jim Gochee's Project Hi-5 Slides](projectFiles/2015 Project Hi-Five Slides/Jim_Gochee_CKO_4_15_FINAL.pptx), slide #7.

Introduce each of the products with a one line description: 
  * APM -- application monitoring with end to end transaction tracing andcode level visibility
  * Servers -- free server monitoring. Speculation: Opsmatic acquisition will bring more value/products to this space
  * Plugins -- monitoring for 3rd party code. Often made by partners. 
  * Browser -- front end performance monitoring (page load, javascript)
  * Synthetics -- application monitoring via automated requests from around the world
  * Mobile -- monitoring apps on mobile devices 
  * Insights -- event driven (not aggregate) data collection and real time data queries

Discuss Application Performance, Customer Experience, Business Success and how it links to products. 

Show APM in use with Demotron using these [instructions](demos/apm_demotron.md).
[Optional] Show Dashboards using these [insturctions](https://newrelic.quip.com/OWpQA71YgCYZ)

## Metrics to Events

Give a bit of the history of what we originally did and how metrics are made, broadcast and used. 

Maybe review the Metrics & Measurements content

Have people on Agent teams maybe talk a bit more about (or assign as homework to learn more about) how their particular agent functions and share with the group.

Can get into the architecture

## New Relic in a Year

Using the [Architecture Vision from 2015-12-02] (projectFiles/Architecture_vision_from_2015-12-02.pdf):
   * slide 3 has the 4 objectives
   * slide 5 -- importance of events
   * slide 6 -- shows that largest data customers have doubled amt of data every year for past 3 yrs. Challenge for data pipeline. We must think of scaling vertially (size of 1 customer's data) and horizontally (more customers)
   * slide 7 -- how will this effect me? 
      * discuss changes in culture -- move from oral 1 to 1 pairing to documented interfaces (for backup, see slide 16 and 17)
      * focus on events
      * importance of data tier (interfaces play a role here)
   * slide 8 - 11 -- future of events and aggregates
   END (no need to discuss the rest of the deck)

## Main Project

Have people do the main project, encourage them to do the top-level only and use Forums & Docs to find answers.


### Synthetics Slides

Before having them setup Synthetics, go over the slides on what Synthetics is and why we use it.


# CEO for the Day  

### Section Objectives

* View dashboards for their teams, modify dashboards for day-to-day queries.
* Analyze New Relic's data to assess a complex scenario

**Pre-Req**: Have students talk to team about their team's dashboards. Potentially do show-n-tell in class the next day

Start the session by reviewing Metrics to Events
   * Question: What are the 3 types of data? Answer: metrics, traces, events
   * Question: What is difference between metrics and events? Answer should involve metrics are time based and aggregated, events discrete non-aggregated chunks of data related to a specific action by the user or code.

Insights uses events data. Insights offers a way to slice through the mass of data gathered by our agents to answer technical and business level questions. 

Demo: Open a raw event (in Insights >> Data Explorer), look at the data contained in that event. How could it be searched, sifted, or sorted?

Insights allows realtime unstructured queries on event data -- not aggregated data points. This means the customer experience (and thus business success) can be tracked on individual level as it happens.
With Insights, you can create queries using NRQL or the Data Explorer and add the results to a dashboard to monitor. Often, to create the correct query, people start with an existing query that is close and then change it. 

 *Use the following dashboards to show queries.* 
 Examples of NR dashboards: 

|  Dashboard  |  Talking points  |  
| -------| ------- | 
| https://insights.newrelic.com/accounts/1/dashboards/82 | Monitors our customer's API usage. Example of traking adoption of feature |  
| https://insights.newrelic.com/apps/accounts/1/ux-what-we-know | Tracking customer usage of new relic. Multiple tabs |  
| https://insights.newrelic.com/accounts/1/dashboards/89822 | Kafka dashboard by Dirac team. This has complicated queries|  
| https://insights.newrelic.com/accounts/1/dashboards/19691 | Lew Cirne’s Business Funnels. Business measures by the CEO! | 

   * What impacts Customer Experience negatively? Answer (amongst others): slow page response time, 
   * What can impact Business Success? Answer (amongst others): lack of revenue, features not adopted/used quickly, 

### Mini-Activity:  
Show-n-tell about one of your team's dashboards. Get at least 3 teams involved. Discuss what it is they're looking for, how they know things are good or bad, and what people should do with that information.

Encourage people to expand the questions answered in a dashboard, maybe modify the search a bit to get to something interesting to them.

### Main Activity - CEO for the Day

Pose N questions to the group, use the group time to gather data, and then have them work on teams to determine the answers. Usually it's best to determine who is/isn't familiar with SQL so that you can make some headway (can't learn SQL in an hour).

Question 1: Where should New Relic put its next 3 data centers?
Question 2: The Board of Directors just told you they want to spend an extra $10M on engineering. Where do you put the money?

Prompts:  
What would we need to know to answer this question? <- Keep repeating that until you get a list of 10+ items.  
Which of these questions could we answer with data from our own systems? <- Go through the list, let them tell you the answers, maybe debate on some of them as it may or may not be clear.

Activity:
Break into teams, have them each work on their answers. There is no right or wrong answer* but it's the exploration and playing with our data that is key.

*ok, there kind of is a right answer...  

A1: On .gov cloud in the USA and in Europe for a data-safe country with good internet connections, and ideally good links to middle east and Asia. Then likely South America or West Coast of USA.

A2: This one is hard without having sales data, PM Roadmaps, and other vision/strategy docs. So maybe keep them focused in the realm of what teams are doing well, which are struggling, where do most of our customers come from, etc. 

Conclusion:  
Have both teams demo what they tried to do, what worked, what didn't, and what they think the answers should be.
