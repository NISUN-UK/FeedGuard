# FeedGuard

Final project for the Building AI course

## Summary

FeedGuard is an AI-powered browser extension that scans social media content in real-time to flag potential misinformation and manipulative advertising, helping users make more informed decisions online. It would cross validate each post with real events, any published lists and databases, and mark the posts based on likelyhood of misinformation.

![Illustration of FeedGuard](ChatGPT%20Image%20Jun%2017,%202025,%2011_19_27%20AM.png)

## Background

Misinformation and manipulative advertising are major problems in the digital age, particularly as posts can now be made in second with misleading photos with AI. From false medical advice to psychologically exploitative political ads, social media feeds often include content designed to deceive or manipulate users.

This idea aims to address:
* The rise in misinformation, particularly during crises (e.g. pandemics, elections)
* The subtle targeting tactics used in ads based on user profiles and fears
* The lack of transparency in how content is prioritised and monetised

I'm interested in how technology can protect users without censoring them. I believe exploring this concept highlights important ethical, social, and technical tensions in AI.


## How is it used?

FeedGuard would be used as a browser plugin or app that runs in the background while a user scrolls social media feeds. It would:
* Flag content with markers (e.g., ⚠️“Likely Misinformation” or 🧠“Manipulative Ad”)
* Provide a brief explanation: e.g., “This post contradicts WHO data” or “This ad uses emotional targeting patterns”
* Let users click for sources or alternative viewpoints

The system would be primarily used by socially-conscious users, educators, parents, and journalists. Its design would need to respect privacy, avoid bias, and be transparent about how it makes judgments. If the extension would gather information about misinformation, it would be imperative that this would be clearly communicated from the outset.

## Code samples:

Here you can see some basic code for the initial flaging of a post:

### Simple demo: Flag social media posts using suspicious keywords

def flag_post(post):
    flagged_keywords = [
        "cure", "miracle", "hoax", "secret", "banned", "exposed", "underground",
        "they don't want you to know", "government coverup"
    ]

    for keyword in flagged_keywords:
        if keyword.lower() in post.lower():
            return f"⚠️ Warning: Post may contain misinformation (flagged: '{keyword}')"
    
    return "✅ Post appears safe"

#### Test examples
posts = [
    "This miracle cure will change your life!",
    "Here's how to bake banana bread",
    "Government coverup exposed in new documentary",
    "Cats are cute. That's it."
]

for post in posts:
    print(post)
    print(flag_post(post))
    print("------")

### Sentiment Analysis Lite
from textblob import TextBlob

def analyse_sentiment(post):
    blob = TextBlob(post)
    polarity = blob.sentiment.polarity
    if polarity > 0.5:
        return "🧠 This post may be emotionally manipulative (very positive tone)"
    elif polarity < -0.5:
        return "🧠 This post may be emotionally manipulative (very negative tone)"
    else:
        return "🟢 Tone appears neutral"

#### Test posts
posts = [
    "Everyone is LYING to you, the truth is terrifying!",
    "This will make you feel amazing. Try it now!",
    "Here's how you can organise your workspace",
]

for post in posts:
    print(post)
    print(analyse_sentiment(post))
    print("------")


## Data Sources:

* Datasets of previously labeled misinformation (e.g., from fact-checking organisations like Snopes, Full Fact, Poynter)
* Ad libraries from Facebook, TikTok, YouTube, etc.
* Natural language corpora showing rhetorical manipulation patterns
* Social media APIs (public posts only, respecting privacy)

## AI Techniques:

* Natural Language Processing (NLP) for detecting false or emotionally manipulative language
* Sentiment analysis and argumentation mining
* Explainable AI (XAI) techniques to justify decisions
* Possibly reinforcement learning to adapt based on user feedback


## Challenges

This project cannot guarantee that all flagged content is harmful — mistakes are inevitable.

Key limitations:
* AI bias: The system may reflect the views of its training data.
* Freedom of speech: Users may reject or distrust warnings.
* Evolving misinformation: False claims constantly adapt to avoid detection.
* Data access: APIs and content from private platforms are limited.

It’s also ethically challenging to balance truth detection with user autonomy and platform responsibility.

## What next?

FeedGuard could evolve into:
* A customisable assistant that explains *why* a post is flagged
* A plugin for educators to use during media literacy lessons
* A public awareness campaign to build critical reading skills

It would need an interdisciplinary team of AI developers, journalists, psychologists, and ethicists. A large, diverse dataset would also be crucial.

## Acknowledgments

* Inspired by browser tools like [NewsGuard](https://www.newsguardtech.com/) and academic work on AI bias.
* Fact-check datasets: Snopes, Poynter, Full Fact.
