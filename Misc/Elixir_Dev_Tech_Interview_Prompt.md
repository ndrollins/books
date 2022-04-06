As a next step to the interview process we'd like you to solve a programming problem. You'll be writing your solution in Elixir. If you need an environment you can use Repl.it or Cloud9, we just ask you to not share your solution publicly, or take them down after you're done if it's hosted somewhere for others to search/see.

### Time "Limit"

We also ask you to limit your time spent solving this problem to an hour or so; again we're not enforcing this in any way except the honesty system. At work, we don't follow people around with stopwatches, so we won't do it here either. Our reasoning for requesting that you limit the time you spend on this problem is simply this: we understand that any free time that you have is ***valuable*** and, in keeping that in mind, we'd like to minimize the impact we have on it.

### Submitting your Solution

Given that we are requesting that you work within an hour-long span, you should feel completely comfortable submitting your solution in whatever state it's at -- partial, pseudo-code, riddled with typos, etc. -- upon the hour's conclusion. That's ok. If you end up spending significantly more time (again, not encouraged), please let us know when you submit your solution. Please send any/all files files that your solution is comprised of back to us, via e-mail.

## The Problem

Imagine you have recently written a new language for Annkissam and collected all words into the Annkissam Dictionary. Similar to the English language, words can be categorized as nouns, verbs, and articles.

Below is the list of words (categorized by part of speech) that make up the Annkissam Dictionary:

- Nouns: "abcd", "c", "def", "h", "ij", "cde"
- Verbs: "bc", "fg", "g", "hij", "bcd"
- Articles: "a", "ac", "e"

To assist with the more interesting part of this problem, we'll provide you with the the following *basic* module (`Annkissam.Dictionary`) that you can make use of and/or adjust as you see fit:


```elixir
defmodule Annkissam.Dictionary do
  @moduledoc """
  Dictionary module that acts as a repository for the various words --
  categorized by their various parts of speach -- which together
  form the basis of the Annkissam language.
  """
  @articles ["a", "ac", "e", "jkl"]
  @nouns ["abcd", "c", "def", "h", "ij", "cde", "jkl"]
  @verbs ["bc", "fg", "g", "hij", "bcd", "jkl"]
end
```

The rules for composing a sentence in the Annkissam Language vary (quite dramatically) from what you'll find in most other languages. A valid sentence in the Annkissam Language must adhere to the following set of rules:

1. All of a sentence's words must be present in the Annkissam Dictionary.
2. A sentence must contain **at least one** verb.
3. A sentence must contain *either* **at least one** noun *or* contain **at least two** articles.
4. The order of the words within the sentence **does not matter**.

These rules, With the contents of the Annkissam Dictionary (see above)

To help clarify, the following are ***examples of valid sentences***:

- "abcd bc" <-- 1 noun; 1 verb (see Rule 2, above)
- "bc abcd" <-- 1 noun; 1 verb (provided to illustrate that order doesn't matter (see Rule 4, above)
- "bc a ac" <-- 1 verb; 2 articles (see Rule 3, above)
- "a bc def g" <-- 1 verb; 1 noun; 2 articles

The following, on the other hand, are **examples of invalid sentences**:

- "abcd" <-- 1 noun; 0 verbs
- "bc" <-- 1 noun; 0 verbs
- "bc a" <-- 1 verb; 1 article
- "x" <-- word not in dictionary (see Rule 1, above)

Your task is to write a sentence composer which will take a single string as an input, split it into words, and return all of the possible valid sentences that can be constructed using those words (as a list of strings).

The sentences returned by the composer should maintain the character ordering of the input string and insert, at most, one space (" ") between characters as necessary to create a set of valid words that, when combined, constitute a valid sentence.

For example, the input "bcaa" can be split into the words "bc", "a", and "a", which constitute a valid sentence ("bc a a").

The input "aa", can be split into "a" and "a", but that is not a valid sentence ("a a").

Finally, "abcd" can be split into multiple combinations of words, however these word combinations cannot be combined to produce a valid sentence:
- "a", "bcd" --> combination of these words yields the following invalid sentence: "a bcd"
- "abcd" --> invalid sentence (no combination necessary since it's a single term)

Here's a skeleton module (`Annkissam.Language`) for you to adjust to accomplish the objective.

```elixir
defmodule Annkissam.Language do
  @moduledoc """
  Language module that is used to compose sentences via referencing words defined
  by the `Annkissam.Dictionary` module.
  """

  # Insert your code here ;)
end
```

Please write tests to back up your solution and submit them as well; they can be in the same file as the solution. Feel free to use ExUnit or plain raise assertions.

*Note: Please make sure to list any/all assumptions you make.*

### A few examples

For your convenience, we have provided some sample inputs that, when provided to
the composer, yield the corresponding outputs:

##### Example 1

Input = "abcdefg", should return the following list:

```elixir
[
  "a bc def g",
  "a bcd e fg",
  "abcd e fg"
]
```

##### Example 2

Input = "abcc", should return the following list:

```elixir
["a bc c"]
```

##### Example 3

Input = "abcd", should return the following list:

```elixir
[]
```