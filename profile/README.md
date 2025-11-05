# Reddit Trend Analyzer 

🔥 **No more endless scrolling** – discover what’s trending online and how people feel about it, at a glance

🔍 This application fetches top Reddit posts and uses sentiment analysis to show whether discussions are positive, negative, or neutral

🎓 Developed for **Software Development Project II** at Haaga-Helia University of Applied Sciences

🚧 Currently in early development

## 🛠 Tech Stack
- **Backend:** Flask & Python
- **Frontend:** Next.js & TypeScript

## 🧩 Full Stack Application Overview
```mermaid
flowchart LR
    %% Database
    C1[(**MongoDB Atlas**)]

    %% Connections
    C7 <-- read/write data --> C1
    E12 --> C1
    E22 --> C1
    E32 --> C1
    E34 --> C1
    E4 <--> C1

    subgraph C[Flask backend]
        C7[**REST API**:<br/>topics, country data, statistics, authentication, subscriptions...]
    end
    B4 <-- API requests --> C7

    %% Automated pipelines
    subgraph E[Automated data pipelines - GitHub Actions]
        X[**GitHub Actions**]
        X -- runs daily --> E1
        X -- runs daily --> E2
        X -- runs daily --> E3

        E1[**Trending topics analysis pipeline**]
        E2[**Country subreddit analysis pipeline**]
        E3[**Subscription-based analysis pipeline**]
        E4[**Inactive user check**:<br/>automatic subscription deactivation]

        E1 --> E11[Fetch 500 posts from predefined subreddits] --> E12[Topic modeling, summarization, sentiment analysis]
        E2 --> E21[Fetch 10 posts from predefined country subreddits] --> E22[Translation, sentiment analysis]
        E3 -->|Topics analysis| E31[Fetch 500 posts from subscribed subreddits] --> E32[Topic modeling, summarization, sentiment analysis]
        E3 -->|Posts analysis| E33[Fetch 10 posts from subscribed subreddits] --> E34[Sentiment analysis]
        E3 --> E4
    end
  
    %% Next.js
    subgraph B[Next.js app]
        B1[**Route**]
        B2[**page.tsx**]
        B3[**Client components**]
        B4[**Server components**]

        B1 <--> B2
        B2 <--> B3
        B2 <--> B4 
    end

    %% Client node
    A[**Client**] -- Page request --> B[Next.js]
    B[Next.js] -- Page render -->A[**Client**]  
```

## 📌 User Stories

✅ Done | 🟡 Partially done | 🔄 In progress | 🔜 Planned for future sprints | ❔ TBD

| #  | User story | Notes | Sprint | Status |
|----|------------|-------|--------|--------|
| 1  | As a user, I want trending Reddit topics in one place, so that I can quickly see what’s popular. | Initial version with real-time Reddit requests and analysis (BERTopic) developed in Sprint 1. Automated data processing (via GitHub Actions) and database integration added in Sprint 2. | Sprint 1, Sprint 2 | ✅ |
| 2  | As a user, I want to view the sentiment of public discussions (positive, negative, neutral), so that I can understand people’s opinions on a topic. | Implemented with the VADER model in Sprint 1. The same sentiment analysis approach was later reused in new features. | Sprint 1 | ✅ |
| 3  | As a user, I want to see how opinions on a topic change over time, so I can observe how the discussion develops. | Implemented for subreddit-level in Sprint 2. Topic-level analysis planned for upcoming sprints. | Sprint 2 | 🟡 |
| 4  | As a user, I want to search for specific topics, so that I can find opinions on topics I'm interested in. | | | ❔ |
| 5  | As a user, I want to save topics to my account, so that I can follow them and get updates easily. | Added user authentication and subreddit subscription feature with daily automated analyses (via GitHub Actions). | Sprint 3 | ✅ |
| 6  | As a user, I want to receive a weekly summary of my saved topics (via email, for example), so that I can stay updated easily. | | | ❔ |
| 7  | As a user, I want to see trending topics displayed on a map, so that I can compare public discussion in different countries. | Initial version with real-time Reddit requests implemented in Sprint 2. Automated data processing (via GitHub Actions) and database integration added in Sprint 3. | Sprint 2, Sprint 3 | ✅ |
| 8  | As a user, I want to view results from multiple sentiment analysis models, so that I can evaluate their accuracy and reliability. | | | 🔜 |
| 9  | As a user, I want to receive notifications when a topic I follow starts trending again, so that I don’t miss important updates. | | | ❔ |
| 10 | As a user, I want to filter trending topics by category (e.g., politics, technology, sports), so that I can focus on areas that interest me most. | Category = subreddit. User can view analysis results from a predefined list of subreddits. | Sprint 2 | ✅ |
| 11 | As a user, I want to filter trending topics by time (e.g. 24 hours, 2 days, 7 days), so that I can get accurate data on the timespan I'm interested in. | | | ❔ |
| 12 | As a user, I want to see a graph of the amount of posts over time per topic, so I can quickly explore the topic's lifecycle in popularity. | Kind of included in user story 3, extra/optional? | | ❔ |
| 13 | As a user, I want to get a short text summary explaining why a given topic is trending, so I can understand the context better and stay up-to-date with popular topics. | Added topic summaries (with Flan-T5) to explain discussion context, though it doesn’t explicitly explain 'why' the topic is trending. | Sprint 3 | ✅ |
| 14 | As a user, I want to be able to restrict the visibility of results so that I don't see topics that I find boring. | | | ❔ |
| 15 | As a user, I want to be able to filter the visible topics by their sentiment score so that I see positive, negative or neutral topics only. | | Sprint 1 | ✅ |
| 16 | As a user, I want to use the website also with my phone so that I can access content anytime and anywhere. | | | 🔜 |
| 17 | As a user, I want the site to have a responsive, modern and stylish design, so that my user experience is smooth and enjoyable. | Initial version in Sprint 2, will be refined in upcoming sprints | Sprint 2 | 🟡 |
| 18 | As a user, I want to see a clear description of how the data is processed and analysed, so that I can better understand and trust the results. | | | 🔜 |
| 19 | As a developer, I want to perform testing, so that I can ensure the quality of my product. | Started in Sprint 3, and continues in Sprint 4 | Sprint 3, Sprint 4 | 🟡🔄 |


## 📈 Planned Features
Based on user stories:
- View top trending Reddit topics on a single page
- Analyze the sentiment of discussions (positive, negative, neutral)
- Track how opinions change over time and visualize trends
- Filter topics by category, sentiment, or time range
- Compare trending topics and discussions across different countries on a map
- Log in and follow topics of interest to receive updates easily

## 👥 Team and Roles
**The team**: [Kirsi](https://github.com/kkivilahti), [Musakhan](https://github.com/MusaMamas), [Laura](https://github.com/makinla), [Niklas](https://github.com/niklasovaska) & [Artur](https://github.com/dmas5)
  
The team rotates roles and tasks each sprint to ensure a comprehensive learning experience. We don’t have fixed responsibilities — everyone is free to choose tasks based on their interests. Although we have no permanent backend or frontend teams, roles have formed naturally: **Kirsi, Laura, and Artur** have mainly worked on the backend, while **Musakhan and Niklas** have focused on the frontend.

Sprint-specific responsibilities are listed below.

<details>
<summary>Sprint 1</summary>

| Team Member | Area     | Tasks |
|-------------|----------|-------|
| **Kirsi**   | Backend  | - Connect to Reddit API and create initial data fetch for selected subreddits<br>- Perform topic modeling with BERTopic<br>- Documentation |
| **Laura**   | Backend  | - Optimize Reddit API connection using asyncio semaphore<br>- Perform sentiment analysis with VADER<br>- Documentation |
| **Artur**   | Backend  | - Set up initial REST API with CORS configurations |
| **Niklas**  | Frontend | - Initialize Next.js app<br>- Fetch data from backend<br>- Display sentiment analysis results in UI<br>- Documentation |
| **Musakhan**| Frontend | - Display trending topics in the UI<br>- Implement topic filtering based on sentiment values (positive, negative, neutral)<br>- Add error handling and loading states |

</details>

<details>
<summary>Sprint 2</summary>

| Team Member | Area     | Tasks |
|-------------|----------|-------|
| **Kirsi**   | Backend  | - Automate data processing with GitHub Actions<br>- Implement backend logic for category filtering: automated analysis pipeline for selected categories, database integration, and API endpoint for retrieving latest data<br>- Convert topic labels into a more readable form<br>- Documentation |
| **Laura**   | Backend  | - Create backend logic for the map feature: language translation with Flan-T5 and a new API endpoint with real-time Reddit requests and analysis<br>- Documentation |
| **Artur**   | Backend  | - Connect to database<br>- Research options for app deployment |
| **Niklas**  | Backend<br>Frontend | - Plan how to implement over-time analysis<br>- Develop backend logic for over-time analysis: implement MongoDB aggregation queries to calculate statistics for stored data, and add corresponding API endpoints<br>- Create initial version of the map feature in frontend<br>- Display sentiment analysis results with charts<br>- Documentation |
| **Musakhan**| Frontend | - Implement category filtering in frontend<br>- Display over-time analysis results with charts<br>- Design and implement a stylish and responsive UI |

</details>

<details>
<summary>Sprint 3</summary>

| Team Member | Area     | Tasks |
|-------------|----------|-------|
| **Kirsi**   | Backend  | - Automate data processing and integrate database for the map feature<br>- Design and implement subreddit subscription feature in backend: automated data processing for subscribed subreddits, database integration, and API endpoints<br>- Further develop existing data pipelines<br>- Documentation |
| **Laura**   | Backend  | - Enhance topic modeling results with representation model and topic reduction<br>- Implement topic summarization using Flan-T5<br>- Design and implement user authentication in backend: authentication API endpoints, database integration, and basic security and validation<br>- Documentation |
| **Artur**   | Backend  | - Refactor REST API structure |
| **Niklas**  | Frontend | - Implement subreddit subscription feature in frontend<br>- Research testing options<br>- Begin testing on the frontend side |
| **Musakhan**| Frontend | - Update the map in frontend after backend changes<br>- Implement user authentication logic in frontend and create login/register pages<br>- Display topic summaries in the frontend |

</details>

<details>
<summary>Sprint 4</summary>
Coming soon
</details>

