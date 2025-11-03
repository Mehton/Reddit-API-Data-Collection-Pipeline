# Reddit Climate Change Data Collection

## Assignment Overview

This project collects and analyzes Reddit posts related to **climate change** using the **PRAW (Python Reddit API Wrapper)** library.  
The script performs the following tasks:

- Fetches posts from the **“hot”** section of three climate-related subreddits.
- Searches for posts containing a specific keyword (e.g., _“global warming”_).
- Cleans, organizes, and exports the results into a CSV file for analysis.

---

## How to Run

### 1. Prerequisites

This project requires:

- **Python 3.8+**
- A **Reddit account** and an **API application** (to obtain the `client_id`, `client_secret`, and `user_agent`).

### 2. Installation

Clone or download this repository and install the required dependencies using pip:

```
pip install praw pandas numpy python-dotenv
```

### 3. Configuration

Create a file named reddit_api_template.env in the project directory and add the Reddit API credentials:

```
CLIENT_ID=your_client_id_here
CLIENT_SECRET=your_client_secret_here
USER_AGENT=Project_name_used_on_reddit_to_get_the_credentials by u/YourRedditUsername
```

Then, in Python script load them like this:

```
from dotenv import dotenv_values
import os

# Define the path to your .env file.

env_file_path = '/reddit_api_template.env'
```

### 4. Execution

In Jupyter Notebook, simply run all the cells in sequence.

After execution, the program will:

- Fetch “hot” posts from:

  - r/climate

  - r/environment

  - r/sustainability

- Search for posts containing a keyword (e.g., “global warming”).

- Export the combined data into a file named reddit_climate_data.csv.

## Output Description

**Output File**: reddit_climate_data.csv

This file contains all collected Reddit post data.
Each row corresponds to a single Reddit post, cleaned and deduplicated.

| Column           | Description                                         |
| ---------------- | --------------------------------------------------- |
| **title**        | Full title of the Reddit post                       |
| **score**        | Net upvotes (upvotes - downvotes)                   |
| **upvote_ratio** | Ratio of upvotes to total votes (quality proxy)     |
| **num_comments** | Total number of comments                            |
| **author**       | Reddit username of the post author                  |
| **subreddit**    | Subreddit where the post was collected              |
| **url**          | External link (if not a text post)                  |
| **permalink**    | Permanent Reddit URL to the post                    |
| **created_utc**  | Unix timestamp of post creation                     |
| **is_self**      | `True` if text-only post, `False` otherwise         |
| **selftext**     | Body text of the post (truncated to 500 characters) |
| **flair**        | Category or flair tag assigned to the post          |
| **domain**       | Domain of the linked content (e.g., "nytimes.com")  |
| **search_query** | Keyword used to collect the post (for provenance)   |
