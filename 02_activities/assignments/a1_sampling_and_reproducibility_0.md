# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 5000 (from the original 50000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: Valeria Guimaraes

``` 
Part 1 - Simulation function
STEP 1: 
Creating the dataframe with individuals attending events (weddings and brunches)
step 1a: setting the 'traced' column to a nullable boolean type
Randomly infecting individuals based on "ATTACK_RATE"
Initialize the 'traced' column to 'False'

STEP 2:
Primary contact tracing - Indentifying primary traces based on 'Trace_sucess' and updating 'traced' column

STEP 3:
Secondary COntact Tracing - Indentifying secondary traces if the number of traces in an event meets or exceeds 'secondary_trace_threshold' and update the traced column

STEP 4:
Calculating proportions of infection and traced cases attributed to weddings.

STEP 5: 
Run the simulation multiple time (1000) and store results


2. The sample size in this context is 1000 (200 wedding attendees + 800 brunch attendees). A subset of individuals is selected for infection based on the "ATTACK RATE' and then some of the infected individuals are traced based on 'TRACE SUCCESS'


3. In this simulation, the sampling frame consist of all individuals attending the two weedings and brunches. Each individual in the frame can be considered as a unique entry identified by their event type.



Part 2 - Improving Reproducibility and Improvements
```
1. Random Seed: Setting a random seed ensures reproducibility in random processes. 
First, this allows us to include the random seed within the function to ensure reproducibility and ensure that the function can never be called without a seed being determined/set. Second, this allows us to vary the seed for each iteration in the upcoming for loop where the func is called so that we get different simulated results for each iteration of the for loop.

the seed is varied such that it is always 10 more than m, so we never have 2 instances of the seed (a replicated seed) within a given for loop. Each iteration is a unique random simulation based on the function.

2. Explicit parameters: using parameters to define sizes will make it more adaptable and flexible.

3. Boolean Initialization: Initialize the 'traced' column to 'False to avoid using NaN values.


```


## Criteria

|Criteria|Complete|Incomplete|
|--------|----|----|
|Altercation of the code|The code changes made, made it reproducible.|The code is still not reproducible.|
|Description of changes|The author explained the reasonings for the changes made well.|The author did not explain the reasonings for the changes made well.|

## Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `HH:MM AM/PM - DD/MM/YYYY`
* The branch name for your repo should be: `sampling-and-reproducibility`
* What to submit for this assignment:
    * This markdown file (sampling_and_reproducibility.md) should be populated.
    * The `whitby_covid_tracing.py` should be changed.
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sampling/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `sampling-and-reproducibility`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-3-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
