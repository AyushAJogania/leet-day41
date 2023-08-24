# leet-day41

# Text Justification

## Problem Description

Given an array of strings `words` and an integer `maxWidth`, the task is to format the text such that each line has exactly `maxWidth` characters and is fully (left and right) justified. Extra spaces between words should be distributed as evenly as possible. If the number of spaces on a line does not divide evenly between words, the empty slots on the left will be assigned more spaces than the slots on the right. For the last line of text, it should be left-justified, and no extra space is inserted between words.

## Example

**Input:**

```
words = ["This", "is", "an", "example", "of", "text", "justification."]
maxWidth = 16
```

**Output:**

```
[
   "This    is    an",
   "example  of text",
   "justification.  "
]
```

**Input:**

```
words = ["What", "must", "be", "acknowledgment", "shall", "be"]
maxWidth = 16
```

**Output:**

```
[
  "What   must   be",
  "acknowledgment  ",
  "shall be        "
]
```

## Approach

1. Initialize an empty vector `result` to store the justified lines.
2. Initialize variables `n` as the total number of words and `i` as the current word index.
3. Iterate while `i` is less than `n`:
   - Initialize `lineStart` as `i` and `lineLength` as the length of `words[i]`.
   - Increment `i`.
   - Inside a nested loop, keep adding words to the current line until adding the next word would exceed the maximum width:
     - Increment `lineLength` by the length of `words[i]`.
     - Increment `i`.
4. Calculate `numWords` as `i - lineStart` and `numSpaces` as `maxWidth - lineLength`.
5. Construct the current line:
   - Start with `line` as `words[lineStart]`.
   - If `numWords` is 1 or it's the last line, left-justify the words and fill any remaining space with spaces.
   - If not, calculate the `spaceBetweenWords` and `extraSpaces` needed and distribute them evenly between the words.
   - Add the constructed line to the `result` vector.
6. Return the `result` vector.

## Complexity Analysis

- Time Complexity: O(n), where n is the number of words. We iterate through the words only once.
- Space Complexity: O(n), as we use a result vector to store the justified lines.
