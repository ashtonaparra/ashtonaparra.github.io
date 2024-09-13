---
layout: essay
type: essay
title: "Two Sides of The Coin"
# All dates must be YYYY-MM-DD format!
date: 2015-09-12
published: true
labels:
  - Questions
  - Answers
  - StackOverflow
---

<img width="300px" class="rounded float-start pe-4" src="../img/think.png">

Asking smart questions is vital for software engineers, particularly in open-source communities or forums like StackOverflow. Smart questions clearly define the problem, show prior research and efforts, and invite meaningful discussion. Eric Raymond, in his essay "How to Ask Questions the Smart Way," emphasizes that well-posed questions lead to better responses, more effective collaboration, and higher-quality answers. In this essay, I will analyze one well-crafted question and one poorly posed question from StackOverflow to highlight how these principles impact the kind of help that is received.

## The Smart Question

Question Summary: The smart question is titled “Why is processing a sorted array faster than processing an unsorted array?”. The user asks why a specific behavior is observed when sorting arrays in C++. The developer provides a clear description of their environment and experience: they had been testing performance in C++, found that processing a sorted array was consistently faster, and wanted to understand the reason behind this observation.

```cpp
Q: Why is processing a sorted array faster than processing an unsorted array?

In this C++ code, sorting the data (before the timed region) makes the primary loop ~6x faster:

#include <algorithm>
#include <ctime>
#include <iostream>

int main()
{
    // Generate data
    const unsigned arraySize = 32768;
    int data[arraySize];

    for (unsigned c = 0; c < arraySize; ++c)
        data[c] = std::rand() % 256;

    // !!! With this, the next loop runs faster.
    std::sort(data, data + arraySize);

    // Test
    clock_t start = clock();
    long long sum = 0;
    for (unsigned i = 0; i < 100000; ++i)
    {
        for (unsigned c = 0; c < arraySize; ++c)
        {   // Primary loop.
            if (data[c] >= 128)
                sum += data[c];
        }
    }

    double elapsedTime = static_cast<double>(clock()-start) / CLOCKS_PER_SEC;

    std::cout << elapsedTime << '\n';
    std::cout << "sum = " << sum << '\n';
}

Without std::sort(data, data + arraySize);, the code runs in 11.54 seconds.
With the sorted data, the code runs in 1.93 seconds.
```

Analysis: This question is smart for several reasons:
Specificity: The question is focused on a specific technical issue—array processing speeds in C++—with sufficient background detail.
Effort: The asker mentions having already tested different cases and even provides sample code. This demonstrates they’ve put effort into understanding the problem before seeking help.
Clarity: The user clearly explains the context, the results they are seeing, and what they are struggling to comprehend, making it easier for others to step in with useful responses.

Response Analysis: The answers reflect the smartness of the question. They are high-quality, detailed, and efficiently guide the user to the concept of CPU caching and memory access patterns, which are crucial factors affecting performance. The top-rated answer provides code snippets and links to additional resources to explain the technical aspects of how modern processors cache data.
Outcome: Because the question was well-formed, it sparked a detailed and enlightening discussion. The conversation not only solved the problem for the original asker but also provided valuable insights for many others interested in similar performance optimization issues.

## The Not So Smart Question

Question Summary: The second question is titled “How to insert one string into the middle of another string?”. Here, the user is asking how to insert a string into the middle of another string using Python. However, the question lacks context, clarity, and any sign of effort. The developer simply states what they want to achieve without any details about their code, what they've tried, or the difficulties they've encountered.

```java
Q: How to insert one string into the middle of another string?

I am trying to stick one string into the middle of another string, ex:
Like this:

String One = "MonkeyPony";
String Two = "Monkey";

How would I put String Two into String One so it would read something like MonkeMonkeyyPony?

What I'm trying to do is insert "Monkey" into the middle of "MonkeyPony" numerous times, so on the first time it would read "MonkeMonkeyyPony", and on the second time it would read "MonkeMonMonkeykeyyPony", etc.

```
 
Analysis: This question violates many of Raymond’s principles:
Vagueness: The question is extremely vague. There is no clear explanation of the problem context, and the lack of specifics makes it difficult to offer a precise solution.
No Prior Effort: The user doesn't show any attempt to solve the problem themselves. They haven’t posted any code or mentioned any research, which gives the impression they are relying entirely on the community to figure out the basics.
Poor Engagement: There’s no attempt to foster meaningful dialogue or encourage further exploration of the topic, limiting the potential for a deeper, more productive discussion.

Response Analysis: The responses reflect the lack of effort in the question. Most answers are short and direct, with the top response simply providing a basic code snippet to solve the problem. While this does technically answer the question, it doesn’t engage with the asker in a meaningful way. The responses are largely utilitarian, lacking the depth and insight typically found in discussions about more complex or well-formulated questions.

Outcome: The outcome here is a simple solution, but the interaction lacks educational value. The user gets their answer, but there’s little insight or knowledge gained beyond the immediate fix. This is a missed opportunity for both the asker and the broader community, as the question and its answers don’t stimulate further exploration or understanding.

## Key Insights
Effort and Preparation Matter: As seen in the smart question, the more effort you put into asking a thoughtful question, the better responses you’re likely to receive. Software engineers, especially in collaborative environments, are more inclined to help when they see that the asker has made an effort.
Clarity is Crucial: Clarity in questions not only helps the asker receive better responses but also ensures that the responses are useful to others in the community. A well-explained question can turn a personal problem into a shared learning experience.
Engagement Drives Better Answers: Thought-provoking questions that engage the community tend to elicit deeper, more detailed responses. Conversely, vague or lazy questions often receive minimalist answers that fail to add significant value to the conversation.

## Conclusion

Asking smart questions is a crucial communication skill for software engineers, especially in collaborative environments like StackOverflow. Smart questions demonstrate effort, clarity, and a willingness to engage in meaningful dialogue, which often leads to better, more detailed responses. On the other hand, poorly posed questions limit the learning potential and tend to produce lackluster answers. By adhering to the principles outlined by Eric Raymond, developers can ensure that their interactions lead to more effective and rewarding problem-solving experiences for both themselves and the broader community.
