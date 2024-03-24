# Generative AI For Everyone
  + [week 1](#week-1)
  + [week 2](#week-2)
  + [week 3](#week-3)
  + [quiz](#quiz)

---
## Week 1
### What is Generate AI?
### Generative AI Applications
**`Writing`**
  + Brainstorming partner (Brainstorming product name, developing sales strategy, ...)
  + Writing some copy (Writing a press release, ...)
  + Translation

**`Reading`**  
  + Proofreading (Correct grammar, ...)
  + Summarize (Summarizing an article, ...)
    + Use case: Summarizing call center conversations
    ```
     [Record phone call] => [A Speech Recognition] => [LLM Summary Conversations] => [Reports]
    ```
  + Email Routing, Sentiment Analysis

**`Chating`**
  + Customer service
  + Specialized ChatBots (Trip planner, Career coaching advice, ...) 
  + IT Service ChatBot

  The range of the spectrum of common design (text-based chatbot)
  + Humans only
  + Bots support humans (human-in-the-loop)
  + Bot triages for humans
  + Chatbots only

  Advice for deploying chatbots
  1. Start with an internal-facing chatbot
  2. Deploy with human-in-the-loop to check for mistakes
  3. Only after deemed safe, allow the bot to communicate directly with customers

**`What LLMs can and cannot do`**
  + LLMs are a useful mental model for comparing LLMs' abilities to those of a *fresh college graduate* with general background knowledge but no specific training.
  + Knowledge cutoff - is frozen at the time of its training
  + Hallucinations
  + Technical limitation
    + the context length
    + doesn't work well with structured data (tabular data, ...), works best with unstructured data (text, image, audio, video, ...)
  + Bias and Toxicity - that exist in the text it learned from

**`Tips for prompting`**
  + **Be detailed and specific** - Providing ample context and clear instructions ensures the LLM understands the task
    ```
    [Write an email]
    Help me write an email asking to be assigned to the legal documents project

    I'm applying for a job on the legal documents project, which will check legal documents using LLMs. I have ample experience promting LLMs to generate accurate text in a professional tone.

    Write a paragraph of text explaining why my background makes me a strong candidate to this project and advocate for my candidacy.
    ```

  + **Guide the model to think through its answer** - Offering step-by-step instructions can help steer the model toward the desired output
  ``` 
    [Want a rhyming cat toy name with a relevant emoji]
    Brainstorm 5 names for a new cat toy
    Step 1: Come up with 5 fun, joyful words that relate to cats.
    Step 2: For each word, come up with a rhyming name for a toy.
    Step 3: For each toy name, add a fun, revelant emoji.
  ```
  + **Experiment and iterate** - Prompting is an iterative process. Starting with a basic prompt and refining it based on the initial response helps achieve the desired outcome. It's essential to adjust the prompt as needed until satisfactory results are obtained.
  ```
    Human : Help me rewrite this
    LLM   : [...] # evaluate output and improve prompt
    Human : Correct any grammatical and spelling errors in this
    LLM   : [...] # evaluate output and improve prompt
    Human : Correct any grammatical and spelling errors in this, and rewrite in a tone appropriate for a professional resume:
  ```

**`Image generation`**
  + Diffusion Model (Supervised learning) 
    + https://community.deeplearning.ai/t/is-diffusion-model-supervised-learning-or-unsupervised/497060/5
  + Process
    + training
      + be trained by gradually adding noise to a reference image and then learning to remove this noise.
      + the reference images are paired with descriptions or prompts, allowing the model to understand and generate images based on specific instructions.
    + generate
      + with a prompt, the model is provided with a noisy image, and it gradually refines the image based on the prompt.
      + through several iterations, the noise is progressively removed, resulting in a clear image

---
## Week 2
### Software Applications
  With the supervised learning method, it takes 6-12 months to build and deploy a valuable AI model. In contrast, prompt-based AI methods take hours or maybe days.

**`Lifecycle of a generative AI project`**
  ```
    Scope ---> Build/Improve System ---> Internal Evaluation ---> Deploy and Monitor
  ```

**`Cost intuition`**

The cost associated with using LLMs is based on the number of `tokens` for both the output text and the prompt length

> token is loosely either a word or a subpart of a word

### Advanced technologies: Beyond prompting
**`Retrieval Augmented Generation (RAG)`**
  
  Allows LLMs to incorporate relevant context into their prompts, enabling them to generate more informed and accurate responses to user queries.
  + 3 steps:
    + **Retrieval**: Given the question, search relevant documents for the answer
    + **Augmentation**: Incorporate retrieved text into an updated prompt
    + **Generation**: Generate the answer from the new prompt with additional context

  > Viewing LLMs as reasoning engines rather than mere knowledge stores, highlighting the potential for LLMs to process and reason through information rather than simply retrieve it. 

**`Fine-Tuning`**

  Provide LLMs with additional information beyond what they learn from the internet. It involves modifying an LLM's outputs to align with a specific style or domain of knowledge.
  + cons:
    + useful for tasks that are challenging to define in a prompt, such as  
      + generating specific summaries
      + mimicking a particular writing style.
    + help LLM gain specific knowledge
    + allows for the optimization of smaller models to perform the task 
      + low cost/latency to deploy 
      + can run on mobile/laptop (edge devices)

  > Fine-tuning can be done well with 1000 to 10,000 examples.

**`Pretraining`**

  Pretraining is a cost endeavor, often requiring tens of millions of dollars, a dedicated engineering team, several months, and a vast amount of data.

  + Bloomberg - successfully pre-trained models with finance domain
  https://github.com/AI4Finance-Foundation/FinGPT

**`Instruction tuning and RLHF`**

  Enables LLMs to follow specific instructions rather than simply predicting the next word based on internet text.

  RLHF
  ```
      LLM   ----- response ----> HUMAN (score) ---- training -----> Reward Model
        |                                                                 |
        |                                                                 |
        |<----------------- fine-tuning ----------------------------------|
  ```

**`Choosing a model`**
  + Model Size

  |Size        |Description                                          |Purpose|
  |------------|-----------------------------------------------------|-------|
  |1B params   |Pattern matching and basic knowledge of the word     |Restaurant review sentiment|
  |10B params  |Greater world knowledge. Can follow basic instruction|Food order chatbot|
  |100B+ params|Rick world knowledge. Complex reasoning              |Brainstorming partner|

  > Experimentation is key. The performance of an LLM can vary based on the specific task and data

  + Closed/Open Source?

  |Closed-Source Models       |Open-Source Models                           |
  |---------------------------|---------------------------------------------|
  |Easy to use in applications|Full control over model                      |
  |More large/powerful models |Can run on your own device (on-prem, PC, etc)|
  |Relatively inexpensive     |Full control over data privacy/access        |
  |Some risk of vendor lock-in|                                             |

---
## Week 3
### Generative AI and Business
**`Generative AI in Business and Society`**

  Generative AI, being a versatile technology
  + Marketers use it for brainstorming email campaign ideas
  + Recruiters use it for summarizing job candidate reviews
  + Programmers utilize it for generating initial drafts of code
  + Andrew Ng used it as a thought partner for problem-solving

  > It's important to double-check the output, especially for critical tasks, as LLMs may sometimes generate errors

**`Task analysis of jobs`**
  > Rather than viewing AI as automating entire jobs, it's more practical to consider it as automating individual tasks within job

  > For some tasks, businesses will start with augmentation and gradually move toward automation

  How do you evaluate the different tasks for generative AI potential?
  + Technical feasibility
    + can AI do it?
    + how costly is it to build an AI system to do it?
  + Business value
    + how valuable is it for AI to augment or automate this task?

  > The misconception that AI implementation is primarily about cost savings. Instead, businesses should focus on leveraging AI to drive revenue growth by rethinking workflows and creating new value propositions.

**`Teams to build generative AI software`**
  + Software engineer
    + Responsible for writing software application 
    + Ideally, someone who has learned the basics of LLMs/prompting
  + Machine learning engineer
    + Responsible for implementing AI system
    + Ideally familiar with LLMs/prompting, RAG, fine-tuning
  + Product Manager
    + Responsible for identifying and scoping the project
  + Prompt engineer? (not as prevalent in practice)
  + Data engineer [large team]
    + Responsible for organizing data and ensuring data quality
  + Data scientist [large team]
    + Responsible for analyzing data to make recommendations to guide project or business decisions
  + Machine learning researcher
    + Responsible for developing advanced AI technologies

> Overall, the statistic underscores that much of the impact of generative AI will be on knowledge workers, who primarily generate value through their knowledge, expertise, critical thinking, and interpersonal skills

### Generative AI and Society
**`Concern about AI`**
  + Amplifying humanity's worst impulses (improve through fine-tuning and RLHF)
  + Job loss
  + Human extinction

**`Artificial General Intelligence (AGI)`**
  AI that can do any intellectual task that a human can

**`Responsible AI`**
  
  Key dimensions:
  + Fairness: Ensuring AI does not perpetuate or amplify biases
  + Transparency: Making AI systems and their decisions understandable to stakeholders impacted
  + Privacy: Protecting user data and ensuring confidentiality
  + Security: Safeguard AI systems from malicious attack
  + Ethical Use: Ensuring AI is used for beneficial purposes

---
## Quiz
### What is Generative AI?
1. Which of these is the best definition of “Generative AI”? <br/>
```
  A. A form of web search.
  B. Any web-based application that generates text.
  C. AI that can produce high quality content, such as text, images, and audio.
  D. Artificial intelligence systems that can map from an input A to an output B.
```
<details>
  <summary>Answer: </summary>
  <b>[C]</b> - Generative AI refers to a collection of tools that can generate high-quality text, images, and audio, including large language models (LLMs) and diffusion models for image generation.
</details> </br>

2. Which of these is the most accurate description of an LLM?
```
  A. It generates text by using supervised learning to carry out web search.
  B. It generates text by repeatedly predicting the next word.  
  C. It generates text by repeatedly predicting words in random order.
  D. It generates text by finding a writing partner to work with you.
```
<details>
  <summary>Answer: </summary>
  <b>[B]</b> - A Large Language Model (LLM) has been trained to repeatedly predict the next word using 100 billion - trillions of examples of text from the internet.
</details> </br>

3. True or False. Because an LLM has learned from web pages on the internet, its answers are always more trustworthy than what you will find on the internet. 
```
  A. True
  B. False
```
<details>
  <summary>Answer: </summary>
  <b>[B]</b> - Because LLMs can hallucinate (make facts), it is best to fact-check the response from an LLM before using it in situations where factual accuracy is important.
</details> </br>

4. Why do we call AI a general-purpose technology?
``` 
  A. Because it is useful for many different tasks.
  B. Because it can chat.
  C. Because it includes both supervised learning and generative AI.
  D. Because it can be accessed via the general web.
```
<details>
  <summary>Answer: </summary>
  <b>[A]</b> - General purpose technologies are, by definition, designed to be versatile and useful for a wide range of tasks. This broad utility across various applications is what characterizes AI as a general-purpose technology.
</details> </br>

5. You hear of a company using an LLM to automatically route emails to the right department. Which of these use cases is it most likely to be?
```
  A. The company has a software-based application that uses an LLM to automatically route emails.
  B. Employees are copy-pasting the emails into a web interface to decide how to route them.
```
<details>
  <summary>Answer: </summary>
  <b>[A]</b> - A software-based application that uses an LLM to automatically read and route emails can process many emails automatically as they are received. So it is most likely the company is using a software-based application to carry out this work.
</details> </br>

### Generative AI applications
1. A friend writes the following prompt to a web-based LLM: “Write a description of our new dog food product.” <br/>
Which of these are reasonable suggestions for how to improve this prompt?
```
  A. Give the LLM more context about what’s interesting or unique about the product to help it craft a better description.
  B. Give it guidance on the purpose of the description (is it to go in an internal company memo, a website, a press release?) to help it use the right tone.
  C. Specify the desired length of the description.
  D. All of the above.
```
<details>
  <summary>Answer: </summary>
  <b>[D]</b> - Providing as many details as you can about the task you are trying to carry out in the prompt helps the LLM generate a response that is closer to what you want.
</details> </br>

2. Which of the following are tasks that LLMs can do? (Check all that apply)
```
  A. Summarize articles.
  B. Translate text between languages.
  C. Earn a university degree (similar to a fresh college graduate).
  D. Proofread text that you’re writing.
```
<details>
  <summary>Answer: </summary>
  <b>[A]</b> - LLMs can take long texts as input and output shorter summaries of those texts.</br>
  <b>[B]</b> - LLMs can produce high-quality translations for widely-spoken languages that have lots of text on the internet (also known as “high resource” languages).</br>
  <b>[D]</b> - LLMs can be used for proofreading tasks on text that you are writing, like correcting spelling and grammar mistakes, and editing for length or clarity.</br>
</details> </br>

3. Someone prompts an LLM as follows: “Please summarize each of this morning’s top 10 news stories in 100 words per story, in a manner suitable for a newsletter.” What is the main reason this is unlikely to work?
```
  A. Because of the knowledge cutoff, the LLM will not have access to the latest news.
  B. The output length is limited, and 10 stories is too many.
  C. Asking for a list of 10 items means we’re working with structured data, which an LLM is poor at.
  D. The prompt needs to give more context about what type of newsletter it is (tech, general news, etc).
```
<details>
  <summary>Answer: </summary>
  <b>[A]</b> - An LLM's knowledge of the world is frozen at the moment of its training, so it does not have any knowledge of more recent events - including today’s news
</details> </br>

4. You’re preparing a presentation about technology, and ask an LLM to help you find an inspirational quote. It comes up with this:
```
  And that’s what a computer is to me. What a computer is to me is it’s the most remarkable tool that we’ve ever come up with, and it’s the equivalent of a bicycle for our minds. -Steve Jobs 
```
  How should you proceed?
```
  A. LLMs have learned from text on the internet; so you can safely trust that this quote is found on multiple webpages, and use it in your presentation.
  B. Because LLMs hallucinate, double-check this quote by searching other sources (such as the web) to verify if Steve Jobs really said this.
  C. Do not use this quote because an LLM can generate toxic output.
  D. Because LLMs can hallucinate, double-check this quote by prompting the LLM to ask if it is really sure Steve Jobs said this.
```
<details>
  <summary>Answer: </summary>
  <b>[B]</b> - LLMs can generate authoritative-sounding, but factually inaccurate text (a behavior known as “hallucinating”). It is important to double-check its output when factual accuracy is important to your task.
</details> </br>

5. You want an LLM to help check your writing for grammar and style. Which of these is the better approach for creating a prompt?
```
  A. Don’t overthink the initial prompt -- quickly give it some context, then prompt the LLM to get its response, see what you get and iteratively refine your prompt from there.
  B. Take all the time you need to carefully craft a prompt that gives it all the appropriate context, so that it works reliably the first time.
```
<details>
  <summary>Answer: </summary>
  <b>[A]</b> - Prompting is a highly iterative process, and taking your initial idea, prompting the LLM, and then refining your prompt based on the model’s output is the most effective way to get to the output that you want.
</details> </br>

### Software Applications
1. In the videos, we described using either supervised learning or a prompt-based development process to build a restaurant review sentiment classifier. Which of the following statements about prompt-based development is correct?
```
  A. Prompt-based development is generally much faster than supervised learning.
  B. Prompt-based development requires that you collect hundreds or thousands of labeled examples.
  C. Prompt-based development requires that you collect hundreds or thousands of unlabeled examples (meaning reviews without a label B to say if it is positive or negative sentiment).
  D. If you want to classify reviews as positive, neutral, or negative (3 possible outputs) there is no way to write a prompt to do so: An LLM can generate only 2 outputs. 
```
<details>
  <summary>Answer: </summary>
  <b>[A]</b> - Prompt-based development allows you to take advantage of an LLM’s ability to carry out sentiment classification, so you can get up and running very quickly because you don’t need to train a model from scratch.
</details> </br>

2. What is a token in the context of a large language model (LLM)?
```
  A. The part of the LLM output that has primarily symbolic rather than substantive value (as in, “the court issued a token fine”, or “the LLM generated a token output”).
  B. A physical device or digital code to authenticate a user's identity.
  C. A word or part of a word in either the input prompt or LLM output.
  D. A unit of cryptocurrency (like bitcoin or other “crypto tokens”) that you can use to pay for LLM services.
```
<details>
  <summary>Answer: </summary>
  <b>[C]</b> - Tokens in the context of LLMs refer to a unit of text. Common words are typically represented by a single token, while uncommon words may be broken into two or more tokens. 
</details> </br>

3. What are the major steps of the lifecycle of a Generative AI project? 
```
  A. Scope project → Build/improve system → Internal evaluation → Deploy and monitor 
  B. Scope project → Internal evaluation → Build/improve system → Deploy and monitor 
  C. Scope project → Internal evaluation → Deploy and monitor → Build/improve system
```
<details>
  <summary>Answer: </summary>
  <b>[A]</b> - This sequence accurately represents the recommended steps in the lifecycle of a Generative AI project. You first scope the project, then build or improve the system, followed by internal evaluation, and finally, deployment and monitoring.
</details> </br>

4. You are building a customer service chatbot. Why is it important to monitor the performance of the system after it is deployed?
```
  A. Because of the LLM’s knowledge cutoff, we must continuously monitor the knowledge cutoff and update its knowledge frequently.
  B. Every product should be monitored to track customer satisfaction -- this is good practice for all software.
  C. This is false. So long as internal evaluation is done well, further monitoring is not necessary.
  D. In case customers say something that causes the chatbot to respond in an unexpected way, monitoring lets you discover problems and fix them.
```
<details>
  <summary>Answer: </summary>
  <b>[D]</b> - Users can be very creative in the ways they prompt chatbots, so monitoring the system can help you identify any issues with the chatbot’s output as they arise and allow you to improve the system in response.
</details> </br>

5. You are working on using an LLM to summarize research reports. Suppose an average report contains roughly 6,000 words. Approximately how many tokens would it take an LLM to process 6,000 input words? (Assume 1 token = 3/4 words, or equivalently, 1 word \approx 1.333 tokens).
```
  A. 4,500 tokens (6000 * 3/4)
  B. 6,000 tokens 
  C. 8,000 tokens (about 6000 * 1.333) 
  D. 14,000 tokens (about 6000 * 1.333 + the original 6000 words)
```
<details>
  <summary>Answer: </summary>
  <b>[C]</b> - A token typically represents a single common word or a part of the word. This means that a word can represent anywhere between 1 or more tokens. Therefore, an LLM typically requires more tokens to process the input number of words. 
</details> </br>


### Advanced technologies: Beyond prompting
1. True or False. Because of the knowledge cut-off, an LLM cannot answer questions about today’s news. But with RAG to supply articles from the news, it would be able to.
```
  A. True
  B. False
```
<details>
  <summary>Answer: </summary>
  <b>[A]</b> - RAG provides an LLM with additional information and context from external documents that it can reason through to answer a question. So RAG would enable an LLM to answer questions about current news articles.
</details> </br>

2. You want to build an application to answer questions based on information found in your emails. Which of the following is the most appropriate technique?
```
  A. Prompting (without RAG), where we iteratively refine the prompt until the LLM gets the answers right.
  B. RAG, where the LLM is provided additional context based on retrieving emails relevant to your question.
  C. Fine-tuning an LLM on your emails, whereby we take a pre-trained LLM and further train it on your emails. 
  D. Pretraining an LLM on your emails.
```
<details>
  <summary>Answer: </summary>
  <b>[B]</b> - RAG can be used to give an LLM access to new, external sources of information that it can reason through to formulate an answer to your question. So a RAG system that provides access to your emails is the best approach to get an LLM to answer your questions. 
</details> </br>

3. What does the idea of using an LLM as a reasoning engine refer to?
```
  A. This refers to the idea of using an LLM not as a source of information, but to process information (wherein we provide it the context it needs, through techniques like RAG).
  B. The idea of using an LLM to play games (like chess) that require complex reasoning, but having its output moves in the game.
  C. Reasoning engine is another term for RAG.
  D. This refers to pretraining an LLM on a lot of text so that it acquires general reasoning capabilities.
```
<details>
  <summary>Answer: </summary>
  <b>[A]</b> - The ability of LLMs to process information is one of the features that makes them such powerful and useful tools. 
</details> </br> 

4. True or False. By making trusted sources of information available to an LLM via RAG, we can reduce the risk of hallucination.
```
  A. False, because giving the LLM more information only confuses the LLM more and causes it to be more likely to hallucinate.
  B. True, because the LLM is now restricted to outputting paragraphs of text exactly as written in the provided document, which we trust.
  C. False, because the LLM has learned from a lot of text from the internet (perhaps >100 billion words) to hallucinate, so adding one more short piece of text to the prompt as in RAG won’t make any meaningful difference.
  D. True, because RAG allows the LLM to reason through accurate information retrieved from a trusted source to arrive at the correct answer.
```
<details>
  <summary>Answer: </summary>
  <b>[D]</b> - RAG can be used to give an LLM access to new, trusted sources of information that it can reason through to formulate an answer to your question. This helps prevent the model from hallucinating because it doesn’t know the answer. 
</details> </br> 

5. An e-commerce company is building a software application to route emails to the right department (Apparel, Electronics, Home Appliances, etc.) It wants to do so with a small, 1 billion parameter model and needs high accuracy. Which of these is an appropriate technique?
```
  A. Fine-tune a 1 billion parameter model on around 1 billion examples of emails and the appropriate department.
  B. Pretrain a 1 billion parameter model on around 1,000 examples of emails and the appropriate department.
  C. Pretrain a 1 billion parameter model on around 1 billion examples of emails and the appropriate department.
  D. Fine-tune a 1 billion parameter model on around 1,000 examples of emails and the appropriate department.
```
<details>
  <summary>Answer: </summary>
  <b>[D]</b> - Fine-tuning an existing model is an effective way to get it to learn how to correctly route emails to the specific departments in the e-commerce company. Fine-tuning can be done well with 1000 to 10,000 examples.
</details> </br> 

### Generative AI and business
1. Which of these job roles are unlikely to find any use for web UI LLMs?
```
  A. Marketer
  B. Recruiter
  C. Programmer
  D. None of the above
```
<details>
  <summary>Answer: </summary>
  <b>[D]</b> - All of the above roles carry out one or more tasks that could be augmented with a web UI LLM. 
</details> </br> 

2. What is the relation between AI, tasks, and jobs?
```
  A. Jobs are comprised of many tasks. AI automates tasks, rather than jobs.
  B. Tasks are comprised of many jobs. AI automates tasks, rather than jobs.
  C. Jobs are comprised of many tasks. AI automates jobs, rather than tasks.
  D. Tasks are comprised of many jobs. AI automates jobs, rather than tasks.
```
<details>
  <summary>Answer: </summary>
  <b>[A]</b>
</details> </br> 

3. Here are some of the tasks of a retail salesperson from O*NET. Say we decide to use AI to augment (rather than automate) a salesperson's task of recommending merchandise to customers. Which of the following would be an example of this?
```
  A. This has no business value and should not be done.
  B. Build an AI system to suggest products to the salesperson, who then decides what to recommend to the customer. 
  C. Build an AI chatbot that can role-play being a customer to help the salesperson practice having conversations with customers.
  D. Build a chatbot that automatically recommends products that customers can access directly, with no salesperson involved.
```
<details>
  <summary>Answer: </summary>
  <b>[B]</b> - Here the AI is augmenting the work of the salesperson by making suggestions, rather than fully taking over and automating the task.
</details> </br> 

4. When looking for augmentation or automation opportunities, what are the two primary criteria by which to evaluate tasks for generative AI potential? (Check the two that apply.) 
```
  A. Technical feasibility (can AI do it?).
  B. Business value (how valuable is it to automate?).
  C. Whether the task is the iconic, defining task for a job role.
  D. Whether to use prompting, RAG or fine-tuning.
```
<details>
  <summary>Answer: </summary>
  <b>[A]</b> - Asking whether a fresh college graduate can complete the task, or consulting an AI engineer, are two ways to assess the technical feasibility of AI augmentation or automation. </br>
  <b>[B]</b> - Thinking about the time taken to complete a task, and the potential value in doing that task faster, cheaper, or more consistently, can help you assess the business value of AI augmentation or automation.
</details> </br> 

5. What is a quick way to start experimenting with an LLM application development project?
```
  A. Hiring a dedicated prompt engineer.
  B. Forming a large team with specialized roles.
  C. Recruiting a large team of data engineers to organize your data.
  D. Try experimenting and prototyping with a web-based LLM to assess feasibility.
```
<details>
  <summary>Answer: </summary>
  <b>[D]</b> - Experimenting and prototyping with web interfaces is a viable way to get started with LLM application development. This allows you to understand what is feasible before investing more time and resources in growing the project and team.
</details> </br> 

---
### Generative AI and Society
1. Which of the following statements about Reinforcement Learning from Human Feedback (RLHF) are true? 
```
  A. RLHF is a common technique for training a small (say 1B parameter) LLM to do as well as a larger (say 10B parameter) one. 
  B. RLHF helps to align an LLM to human preferences, and can reduce the bias of an LLM’s output.
  C. After applying RLHF, an LLM will reflect a similar degree of bias and toxicity as text on the internet.
  D. RLHF fully addresses all concerns about AI.
```
<details>
  <summary>Answer: </summary>
  <b>[B]</b> - RLHF trains models to produce output that better aligns with human preferences, including honesty, helpfulness, and harmlessness. The process can reduce biases in an LLM's output.
</details> </br> 

2. True or False. Because AI automates tasks, not jobs, absolutely no jobs will disappear because of AI. 
```
  A. True
  B. False
```
<details>
  <summary>Answer: </summary>
  <b>[B]</b> - Even if all of the tasks of a role can’t be completely automated, some jobs may be eliminated as efficiency increases and cost savings can be realized. We must support the individuals who may lose their jobs through safety nets and by creating opportunities for retraining and upskilling. 
</details> </br> 

3. If we manage to build Artificial General Intelligence (AGI) someday, which tasks should AI be capable of performing? (Check all that apply.)
```
  A. Compose the music for a movie soundtrack.
  B. Write a software application to let users manage their household spending budgets.
  C. Learn to drive a car in roughly 20 hours of practice.
  D. Predict the future (such as make stock market and weather predictions) with perfect accuracy.
```
<details>
  <summary>Answer: </summary>
  <b>[A]</b> - By definition, AGI can carry out any intellectual task that a human can do. So it should be able to create music for a movie soundtrack. </br>
  <b>[B]</b> - By definition, AGI can carry out any intellectual task that a human can do. Since software applications like this already exist in the world, the AGI should be able to write one from scratch.</br>
  <b>[C]</b> - By definition, AGI can carry out any intellectual task that a human can do. So it should be able to learn to drive a car in roughly 20 hours, just like a human teenager.</br>
</details> </br> 

4. You are working on a chatbot to serve as a career coach for recent college graduates. Which of the following steps could you take to ensure that your project follows responsible AI? (Check all that apply.)
```
  A. Engage diverse recent college graduates and ask them to offer feedback on the output of your chatbot.
  B. Organize a brainstorming session to identify problems that could arise for users chatting with the career coach.
  C. Allow a single engineer on your team to determine whether the output of the chatbot is helpful, honest, and harmless.
  D. Engage employers (because they are a key stakeholder group) and ask them to offer feedback on the output of your chatbot.
```
<details>
  <summary>Answer: </summary>
  <b>[A]</b> - Working with diverse stakeholders can help you identify problems your team may not recognize, and ensure that the behavior of your chatbot takes into account the perspectives of people from diverse backgrounds. </br>
  <b>[B]</b> - Building a culture that encourages discussion and debate of ethical issues can help you identify problems early in the development phase and avoid issues of bias or toxicity later in the process.</br>
  <b>[D]</b> - Working with all stakeholders can reveal points of view that your team may not have realized and can help identify problems or issues that may have been missed.</br>
</details> </br> 

5. Now that you’ve made it to the end of the course, which of these statements are true? (Please check all, because all apply!) 
```
  A. You understand how Generative AI technology works, and what it can and cannot do. 
  B. You’re well positioned to use Generative AI responsibly to help yourself and others.
  C. You’ve achieved the significant accomplishment of finishing this course.
  D. Andrew is thrilled at your completing, and sends you his warmest thank you and congratulations! 
```
<details>
  <summary>Answer: </summary>
  <b>[A,B,C,D]</b>
</details> </br> 