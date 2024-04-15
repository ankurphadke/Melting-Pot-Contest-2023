![Meltingpot banner](https://images.aicrowd.com/raw_images/challenges/social_media_image_file/1125/e746b944fea2eba9bee6.png)

# [NeurIPS 2023 Meltingpot Challenge](https://www.aicrowd.com/challenges/meltingpot-challenge-2023) - Starter Kit 
[![Discord](https://img.shields.io/discord/565639094860775436.svg)](https://discord.gg/fNRrSvZkry)

This repo is the official NeurIPS 2023 Meltingpot Challenge **Submission template and Starter kit**! Fork the repo to compete now!

**This repo contains**:
*  **Documentation** on how to submit your models to the leaderboard
*  **The procedure** for best practices and information on how we evaluate your agent, etc.
*  **Starter code** for you to get started!

# Table of Contents

- [NeurIPS 2023 Meltingpot Challenge - Starter Kit](#neurips-2023-meltingpot-challenge---starter-kit)
- [Table of Contents](#table-of-contents)
- [Competition Overview](#competition-overview)
- [Baselines](#baselines)
  - [Notes for using the baseline:](#notes-for-using-the-baseline)
- [Getting Started](#getting-started)
- [How to write your own policies?](#how-to-write-your-own-policies)
- [How to start participating?](#how-to-start-participating)
  - [Setup](#setup)
  - [How do I specify my software runtime / dependencies?](#how-do-i-specify-my-software-runtime--dependencies)
  - [What should my code structure be like?](#what-should-my-code-structure-be-like)
  - [How to make a submission?](#how-to-make-a-submission)
- [Other Concepts](#other-concepts)
    - [Evaluation Metrics](#evaluation-metrics)
    - [Time constraints](#time-constraints)
  - [Local Evaluation](#local-evaluation)
  - [Contributing](#contributing)
- [📎 Important links](#-important-links)


#  Competition Overview

Your task is to build creative MARL solutions focused on achieving goals through teamwork, teaching, bargaining, and sanctioning undesirable behaviour. The contest scenarios are designed to elicit cooperation, coordination, reciprocity, and other prosocial behaviours. Success requires agents that balance their individual interests with behaviours that benefit the group, even in the face of unfamiliar partners.

The task is a robust testbed for advancing research on mixed individual motives, generalising populations, and large-scale multi-agent interactions.

The aim of this challenge is to catalyse progress in deployable cooperative AI that complements human prosperity. Together we can build consensus on metrics for coordination, engage the broader AI community, and showcase AI’s immense potential for teamwork.

You'll need to submit policy populations that work on different substrates of the meltingpot environemnt.

# Baselines

To ensure a smooth start, we are providing participants with [baselines](https://github.com/rstrivedi/Melting-Pot-Contest-2023) for training and local evaluation of RLIib based agents on Melting Pot. This will allow you to quickly train basic agents and make a submission using the [submission-starter-kit](https://gitlab.aicrowd.com/aicrowd/challenges/meltingpot-2023/meltingpot-2023-starter-kit) to get on the leaderboard. Coupled with tools designed for debugging and visualization, you can establish a strong foundation and then build upon it to reach unprecedented heights.

To submit your trained rllib models, you can use the [`baseline-submission`](https://gitlab.aicrowd.com/aicrowd/challenges/meltingpot-2023/meltingpot-2023-starter-kit/-/tree/baseline-submission) branch in this starter kit.  

## Notes for using the baseline:
* It is recommended that participants use the melting pot fork provided as a part of the baseline implementation so as to work on a frozen version and better track any issues that you may face during the contest.
* Please open issues on the baseline repository directly for any issues with melting pot code or the RLIib implementations.
* We plan to provide additional support to the baseline implementation over the competition. Hence, it would be useful to check in an sync the fork every few days over next two weeks, especially if you plan to build RLLib agents.


#  Getting Started
1. **Sign up** to join the competition [on the AIcrowd website](https://www.aicrowd.com/challenges/meltingpot-challenge-2023).
3. **Fork** this starter kit repo. You can use [this link](https://gitlab.aicrowd.com/aicrowd/challenges/meltingpot-2023/meltingpot-2023-starter-kit/-/forks/new) to create a fork.
4. **Clone** your forked repo and start developing your policies.
5. **Develop** your policies(s) following the template in [how to write your own policies](#how-to-write-your-own-policies) section.
5. **Develop** your reward function following the template in [how to write your own reward function](#how-to-write-your-own-reward-function) section.
6. [**Submit**](#how-to-make-a-submission) your trained models to [AIcrowd Gitlab](https://gitlab.aicrowd.com) for evaluation [(full instructions below)](#how-to-make-a-submission). The automated evaluation setup will evaluate the submissions on the meltingpot environment and report the metrics on the leaderboard of the competition.


# How to write your own policies?

We recommend that you place the code for all your policies in the `my_policies` directory (though it is not mandatory). You should implement the

- `initial_state`
- `step`

**Add your policy names in** `my_policies/user_config.py`, this is what will be used for the evaluations.
  
Examples are provided in `my_policies/random_policy.py`

The policies should be compatible the with policy interface defined in Meltingpot.

Each agent will recieve only the observation timesteps that are relevant to its own contenxt. You should not try to communicate between agents, except by performing actions, i.e no external communication outside the environment.

# How to start participating?

## Setup

1. **Add your SSH key** to AIcrowd GitLab

You can add your SSH Keys to your GitLab account by going to your profile settings [here](https://gitlab.aicrowd.com/profile/keys). If you do not have SSH Keys, you will first need to [generate one](https://docs.gitlab.com/ee/ssh/README.html#generating-a-new-ssh-key-pair).

2. **Fork the repository**. You can use [this link](https://gitlab.aicrowd.com/aicrowd/challenges/meltingpot-2023/meltingpot-2023-starter-kit/-/forks/new) to create a fork.

2.  **Clone the repository**

    ```
    git clone git@gitlab.aicrowd.com:aicrowd/challenges/meltingpot-2023/meltingpot-2023-starter-kit.git
    ```

3. Install meltingpot using the [fork of meltingpot available in the baselines](https://github.com/rstrivedi/Melting-Pot-Contest-2023/tree/main/meltingpot), this is the recommended way for this competition. Alternatively you can install from pypi with `pip install dm-meltingpot==2.2.0` or the [official meltingpot repository](https://github.com/deepmind/meltingpot/tree/main).

4. Write your own policies as described in [How to write your own policies](#how-to-write-your-own-policies) section.

5. Test your agent locally using `python local_evaluation.py`

6. Make a submission as described in [How to make a submission](#how-to-make-a-submission) section.

## How do I specify my software runtime / dependencies?

We accept submissions with custom runtime, so you don't need to worry about which libraries or framework to pick from.

The configuration files typically include `requirements.txt` (pypi packages), `apt.txt` (apt packages) or even your own `Dockerfile`.

You can check detailed information about the same in the 👉 [runtime.md](docs/runtime.md) file.

## What should my code structure be like?

Please follow the example structure as it is in the starter kit for the code structure.
The different files and directories have following meaning:

```
.
├── aicrowd.json           # Submission meta information - like your username
├── apt.txt                # Linux packages to be installed inside docker image
├── requirements.txt       # Python packages to be installed
├── local_evaluation.py    # Use this to check your agent evaluation flow locally
└── my_policies                 # Place your my_policies related code here
    ├── random_policy.py            # Random policy with the required policy interface
    └── user_config.py              # IMPORTANT: Add names of your substrate specific agents here.
```

Finally, **you must specify an AIcrowd submission JSON in `aicrowd.json` to be scored!** 

The `aicrowd.json` of each submission should contain the following content:

```json
{
  "challenge_id": "meltingpot-challenge-2023",
  "authors": ["your-aicrowd-username"],
  "description": "(optional) description about your awesome policy",
}
```

This JSON is used to map your submission to the challenge - so please remember to use the correct `challenge_id` as specified above.

## How to make a submission?

You can use the submission script `source submit.sh <submission_text>` 

To submit you need to:

1. Accept the [challenge rules](https://www.aicrowd.com/challenges/meltingpot-challenge-2023/challenge_rules)
2. Fork the starter kit and add your solution.
3. Push a tag with the prefix `sumbission-` to your repo.
4. After adding the tag, you should find the submission page in the `issues` page of your repo.

You can find more detailed instructions about how to make submissions here
👉 [submission.md](/docs/submission.md)

**Best of Luck** :tada: :tada:

# Other Concepts
### Evaluation Metrics

The competition will use the focal scores on each scenario as the evaluation metric. The mean focal score per focal agent will be calculated for each scenario. As each substrate has differnent number of scenarios, the scores will be averaged per substrated. Finally the average of all 4 substrates will be considered as the final score, all substrates will get equal weightage. 


### Time constraints

You will be provided with 1 vCPU and 3 GB RAM per focal agent. The resources will typically by soft-constrained using the [Ray framework](https://www.ray.io/), while running all the agents on a single machine with 8 or 16 vCPUs, depending on the scenario. For each scenario, your population needs to complete 4 episodes in 15 minutes. No inter-agent communication is allowed (apart from using the actions to implicitly communicate in the observation space).


## Local Evaluation
- You can run the evaluation protocol for your policies locally without any constraint posed by the challenge to benchmark your agents. See `local_evaluation.py` for details. You can change it as you like, it will **not** be used for the live evaluations.

## Contributing

🙏 You can share your solutions or any other baselines by contributing directly to this repo by opening merge request. We'll update these are branches in the repo that can be directly submitted.

- Add your implemntation as `my_policies/<your_policy>.py`.
- Import it in `user_config.py`
- Test it out using `python local_evaluation.py`.
- Add any documentation for your approach at top of your file.
- Make a submission to check the score.
- Create merge request! 🎉🎉🎉 

# 📎 Important links

- 💪 Challenge Page: https://www.aicrowd.com/challenges/meltingpot-challenge-2023

- 🗣 Discussion Forum: https://discourse.aicrowd.com/c/meltingpot-challenge-2023

- 🏆 Leaderboard: https://www.aicrowd.com/challenges/meltingpot-challenge-2023/leaderboards
