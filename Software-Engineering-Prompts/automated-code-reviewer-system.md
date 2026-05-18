# 📄 Case Study: Automated Code Reviewer & Logical Debugger using Interview Pattern

## 1. The Challenge 🎯
* **Context:** Software development teams often encounter inefficient code blocks that cause execution delays and performance bottlenecks during scale.
* **Problem with Basic Prompts:** Standard prompts like *"Optimize this code"* usually yield quick, superficial syntax fixes while ignoring structural flaws, algorithmic efficiency ($O(n)$ complexity), or environmental constraints.

## 2. The Strategy & Framework Design 🧠
To deliver a production-grade debugging assistant, I implemented a hybrid approach combining the **Interview Pattern** with **Chain-of-Thought (CoT)** reasoning. 

Instead of jumping straight to rewriting code, the prompt forces the LLM to follow a strict diagnostic pipeline:
1. **Phase 1: Discovery & Clarification (Interview):** The AI asks targeted questions about the runtime environment, data scale, and core performance goals.
2. **Phase 3: Contextual Optimization:** It processes user constraints (e.g., specific file sizes or cloud environment limitations) to choose the right data structures.
3. **Phase 3: Algorithmic Refactoring:** It outputs optimized code with a comparative analysis of time and space complexity.

## 3. The Prompt Blueprint 🛠️
*Here is the advanced system architecture prompt developed for this engineering pipeline:*

> "Act as a Senior Software Architect. Your task is to analyze and optimize the user's code for memory leaks, logical bugs, and performance bottlenecks. Do not output any refactored code yet. First, initiate the Interview Pattern by asking 2-3 precise clarifying questions regarding the runtime environment, data volume, and unexpected behaviors. Once I provide the answers, apply Chain-of-Thought reasoning to deliver the optimized code along with a Big-O notation analysis for time and space complexity."

## 4. Empirical Test & Implementation 🚀

### Input Parameters Given during Interview:
* **Data Volume:** 10 MB
* **Environment:** Cloud Server
* **Primary Goal:** Reducing execution time (High Speed)

### Legacy Code (Unoptimized):
```python
def find_user_bad_way(user_ids, target_id):
    unique_users = []
    for u_id in user_ids:
        if u_id not in unique_users:
            unique_users.append(u_id)
            
    for i in range(len(unique_users)):
        if unique_users[i] == target_id:
            return True
            
    return False