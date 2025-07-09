---
layout: post
title: Awakening of Azathoth Project
date: 2024-08-14 11:15 -0400
---

# Disclaimer
  
  - I don't attend UC Berkeley but i do find their disclosure of certain courses very useful. I dont believe one should be subjugated to what's on a syllabus. So at different times, i'll scour through various institiution and find various courses that sounds interesting and just do something whatever that is, whole purpose is to walk away learning something new and profound. 

# Explanation Of The PatternAwareLetterFreqGuesser Method

  - It was encourage to write helper methods, which i did. I wrote two helper methods:
  >  keepOnlyWordsThatMatchPattern()
  >  wordMatchesPattern()


## Lets Begin

```java

	private boolean wordMatchesPattern(String word, String pattern){
		if (word.length() != pattern.length()) {
			return false;
		}
		for (int i = 0;  i < pattern.length(); i++) {
			char patternChar = pattern.charAt(i);
			char wordChar = word.charAt(i);

			if (patternChar != '-' && patternChar != wordChar){
				return false;
			}
		}
		return true;
	}
```
   My thought process was the usual. If the word length does not match the pattern length then the only thing left to happen is a **"IndexOutOfBoundsException"** error or something along that line. 







  nnnnn
   My next question to anyone would be what is an "IndexOutOfBoundsException" error. I will define it simply as trying to access an element at a position in a list, array, or string that doesn’t exist. It happens because you’re asking the program to look for something in a place that’s outside the bounds (limits) of what’s available. When i initial began to learn C programming i had to be cautious of things like **"IndexOutOfBoundsException"** only difference is that it's called **segmentation fault**, shorten version is **seg fault**. 

   Now here's the proper comparison:
   > In Java: we get an **IndexOutOfBoundsException** when you try to access an invalid index in a list, array, or string. It's a built-in exception that Java uses to handle such errors.

   > In C: If someone tries to access an array index that’s out of bounds, they might encounter a **segmentation fault**. This happens because the C language allows _direct memory access_, and accessing memory outside the allocated bounds can lead to undefined behavior, including accessing restricted memory areas, which causes the program to crash.

  Lets continue we first check to see if the word length matches the pattern length, then we continue to iterate over each character in the pattern. By doing so what my intention is to retrieve the corresponding character from the word **(wordChar) and the pattern (patternChar).**  and then check two conditions:

   > Pattern Character is Not a Dash.

   > Pattern Character Doesn’t Match Word Character.

### Why?
   Because if the **patternChar** is not a '-', this means the pattern expects a specific character at this position and if the **patternChar** is not equal to the **wordChar,** then the word does not match the pattern at this position, so the method returns false.

   _**And voila we are done, just like that we have written one helper method so far**_


### Second Method

```java

	public List<String> keepOnlyWordsThatMatchPattern(List<String> words, String pattern) {
		List<String> matchingwords = new ArrayList<>();
		for (String word: words){
			if (wordMatchesPattern(word, pattern)){
				matchingwords.add(word);
			}
		}
		return matchingwords;
	}
```
  This one was as straight forward as ever, we needed an  _ArrayList_  to hold the  _matchingwords_,  so we created one.

  > We use a for loop to go through each word in the words list.

  > For each word, the **wordMatchesPattern method** is called. Which then the method checks if the word fits the given pattern.

  > Then if a word matches the pattern, it’s added to the **matchingWords** list.


