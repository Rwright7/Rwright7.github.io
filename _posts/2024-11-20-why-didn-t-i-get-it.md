---
layout: post
title: Why Didn't I Get It
date: 2024-11-20 18:40 -0500
---

# Background information

### What's a `toString` method?

Simple put it just returns a string that provides a representation of an object's current state.

```java
public String toString() {
	String str = new String();

	for (int i = 0; i < numShelters; i++) {
		str += "\nShelter " + (i+1) + ": " + places[i].toString();
	}

	return str;
	}
```

# Explanation for the above:

The above `toString() method` method generates and returns a string that lists all shelters with their respective details.

Initialization:
```java
String str = new String();
```
This creates an empty `String` object named `str`.

For Loop:
```java
for (int i = 0; i < numShelters; i++) {
	str += "\nShelter " + (i+1) + ": " + places[i].toString();
}
```
The for loop runs from 0 to numShelters - 1, accessing each shelter in the places array.

For each shelter, it appends a new line (`\n`) followed by "Shelter X: " where X is the shelter number (starting from 1). It then adds the string representation of the shelter by calling `places[i].toString()`.

Example: If there are three shelters, the string might look like:

```
Shelter 1: [Shelter Details]
Shelter 2: [Shelter Details]
Shelter 3: [Shelter Details]
```

Return Statement:
```java
return str;
```
After the loop completes, the method returns the fully constructed str containing the list of all shelters and their details.


# Example given in class:

```java
public String toString() {
		String str = new String();

		for (int i = 0; i < numShelters; i++) {
			str = places[i].toString() + "\n";  ---> Logic error
		}
		return str;
	}
```

The question asked was, "What will the `toString()` method print?"

Well, no one answered. There was dead silence for like 3 minutes straight.

We got a hint: there is a logic error within the for loop.

Silence persisted the same way; no one answered.

The professor proceeded to draw out what was stored in each array on the board to give us a better representation.

Finally, she told us that the statement `str = places[i].toString() + "\n";` is missing the `+` in front of the `=`, which means that as the loop goes through the array, it is not concatenating. So, it prints out the last thing stored in the array.

My first question to myself was **"What is the subconscious bias that allowed me to miss such a thing?"**

It should have been blatantly obvious to me, but it wasn't not until, the professor stringed us on.

**My Two Reasonings as to Why What Happened Happened:**

1) Confirmation Bias
2) Familiarity and Routine
3) Pattern Recognition Leading to Oversight

_**Confirmation Bias:**_

**What It Is**: *The tendency to search for, interpret, and remember information in a way that confirms your preconceptions.*

**In My Case**: *I might have been so confident that the loop was correct that i didn't critically evaluate each part of it. Which led to missing the simple mistake of missing the `+` operator.*


_**Familiarity and Routine:**_

**What It Is**: *When one becomes very familiar with a piece of code, they might start to "see" what they expect rather than what's actually there.*

**In my Case**: *By writting similar loops many times, It's common to run through the motions on autopilot, not paying full attention to each line.*

_**Pattern Recognition Leading to Oversight:**_

**What It Is**: *Relying on familiar patterns can sometimes cause you to overlook deviations from those patterns.*

**In my Case**: *Expecting the loop to build a concatenated string led me to overlook the fact that code was replacing the string in each iteration instead.*

Solution:
**Deliberate Analysis - Take time to carefully read and understand each line of code. Alongside not assuming patterns are correct; verify them.**

_**It is impossible for a man to learn what he thinks he already knows." — Epictetus**_




