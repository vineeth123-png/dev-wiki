# Basics of Prompt Engg

## Stuff taken from Advanced Prompt Engg course
The stuff listed below are taken from advanced prompt engg techniques course, hosted on linkedin. Course link - [LinkedIn](https://www.linkedin.com/learning/advanced-prompt-engineering-techniques/zero-shot-and-few-shot-prompting?autoSkip=true&dApp=204528272&leis=MVL&resume=false&u=3322), Github repo - [GitHub repo](https://github.com/LinkedInLearning/advanced-prompt-engineering-techniques-3817061)

- **Reference Prompting** - AI gives a better output, when we share a reference/context to the question we're asking.

- ** Zero-shot & Few-shot Prompting** - The reference to shot here has to do with how many examples you provide. So if you provide no examples, you just ask a question or provide some information with a question, then you're doing a zero shot prompt. But if you provide a pattern of some kinds, or question, answer, question, answer, then you're doing few shots. So each question-answer sequence is a shot. Let me show you how this works. In the exercise files, you'll find 

 - Telling an AI system to go step by step improves its output, or **you can improve it even more by also telling it to take a deep breath.** 
 - If you prefix your request by take a deep breath, it goes through a more in-depth process every time. And it's more likely to produce the correct output if you give it a challenging question like a logic puzzle. So why is this happening? Well, think about the training material that underpins all of these large language models. It's the content on the internet. And if you go on the internet, you'll find tons of information about how to solve complex problems by first taking a deep breath and then going step by step. So when we tell the system to take a deep breath and go step by step, we are invoking patterns in the training material that are very detailed breakdowns of a problem into discreet steps that can be solved, one after the other until the task is solved. So anytime you ask an LLM system, how do I open a door with a broken key in it or pull a cork out of a bottle where the cork broke or do something else and you tell it, take a deep breath and go step by step. It'll give you a far more detailed breakdown with discrete steps every time because it's matching the patterns associated with that language. 

 - **Tree of Thought (ToT) Prompting** - Tree-of-Thought prompting is an advanced prompting technique designed to help language models solve complex, multi-step problems more effectively by exploring multiple reasoning paths, instead of committing to a single chain of reasoning.  
 Example Prompt -  
 Imagine three different experts are answering this question. 
All experts will write down 1 step of their thinking, then share it with the group. 
Then all experts will go on to the next step, etc. 
If any expert realises they're wrong at any point then they leave. 
The question is: 
48 people are riding a bus. On the first stop, 8 passengers get off, and 5 times as many people as the number who got off from the bus get into the bus. On the second stop 21, passengers get off and 3 times fewer passengers get on. How many passengers are riding the bus after the second stop?

- **Directional Stimulus prompting** -  
Summarize the above in 2-3 sentences based on the hint. 
Hint: 

- **Chain of Density (CoD) Prompting** -  
Article: {{ ARTICLE }}
You will generate increasingly concise, entity-dense summaries of the above Article.
Repeat the following 2 steps 5 times.
Step 1. Identify 1-3 informative Entities ("; " delimited) from the Article which are missing from the previously generated summary.
Step 2. Write a new, denser summary of identical length which covers every entity and detail from the previous summary plus the Missing Entities.
A Missing Entity is:
- Relevant: to the main story.
- Specific: descriptive yet concise (5 words or fewer).
- Novel: not in the previous summary.
- Faithful: present in the Article.
- Anywhere: located anywhere in the Article.
Guidelines:
- The first summary should be long (4-5 sentences, ~80 words) yet highly non-specific, containing little information beyond the entities marked as missing. Use overly verbose language and fillers (e.g., "this article discusses") to reach ~80 words.
- Make every word count: rewrite the previous summary to improve flow and make space for additional entities.
- Make space with fusion, compression, and removal of uninformative phrases like "the article discusses".
- The summaries should become highly dense and concise yet self-contained, e.g., easily understood without the Article.
- Missing entities can appear anywhere in the new summary.
- Never drop entities from the previous summary. If space cannot be made, add fewer new entities.

Remember, use the exact same number of words for each summary.

Answer in JSON. The JSON should be a list (length 5) of dictionaries whose keys are "Missing_Entities" and "Denser_Summary".