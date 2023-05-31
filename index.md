---
title: Abstract
feature_text: |
  ## TSE: Code Smells Detection Across Programming Languages
feature_image: "https://picsum.photos/1300/400?image=989"
excerpt: ""
---

The incidence of code smells is often associated with software quality degradation. Several studies present the importance of techniques to detect and tackle the incidence of smells in the source code. However, existing techniques to detect code smells depend on the programming language. Consequently, several programming languages are largely employed by the software community without proper techniques of code smell detection. Our study addresses amplifying the availability of code smell detection techniques to different programming languages through transfer learning. We select five programming languages among the ten most used languages according to StackOverflow: Java, C++, Python, C#, and JavaScript. We extract the datasets for training and testing of deep learning models from 150 open sources projects. Results indicate that transfer learning techniques effectively and efficiently detect code smells regardless of the programming language and complexity of the deep learning architecture used in transfer learning. These findings can help developers and researchers to apply the same code smell detection techniques in different programming languages. 

## Detection Rules

| Code Smell       | Programming Languages                | Rule                                                      |
|------------------|--------------------------------------|-----------------------------------------------------------|
| Complex Method   | Java, C#, C++, JavaScript and Python | CC >= 8                                                   |
| Long Method      | Java, C#, C++ and Python             | (LOC > 50) and (CC > 5)                                   |
| Shotgun Surgery  | Java, C# and C++                     | (CC > 4) and (FanOut > 7)                                 |
| Feature Envy     | Java, C# and C++                     | (CC > 4) and (FanOut > 4) and (LCOM < 30%)         |
| Divergent Change | Java, C# and C++                     | (FanIn > 10) and (LCOM < 50%) and (CC > 4)         |
| God Class        | Java, C#, C++ and Python             | [(LOC > 150) and (CBO > 6)] or [(NOM > 15) and (CBO > 6)] |

<br />

## Metrics 

| Name | Understand | Description |
|---|---|---|
| Cyclomatic Complexity (CC) | Cyclomatic | McCabe Cyclomatic complexity as per the original NIST paper on the subject. The cyclomatic complexity of any structured program with only one entrance point and one exit point is equal to the number of decision points contained in that program plus one. Understand counts the keywords for decision points (FOR, WHILE, etc) and then adds 1. For a switch statement, each 'case' is counted as 1. For languages with Macros, the expanded Macro text is also included in the calculation. |
| Number of Lines (LOC) | CountLine | Number of physical lines. |
| Number of Methods (NOM) | CountDeclMethod | Number of local (not inherited) methods. |
| FanIn | CountInput | The number of inputs a function uses plus the number of unique subprograms calling the function. Inputs include parameters and global variables that are used in the function, so Functions calledby + Parameters read + Global Variables read. Of the two general approachs to calculating FANIN (informational versus structural) ours is the informational approach. |
| FanOut | CountOutput | The number of outputs that are SET. This can be parameters or global variables. So Functions calls + Parameters set/modify + Global Varibales set/modify. Of the two general approachs to calculating FANOUT (informational versus structural) ours is the informational approach. |
| Coupling Between Objects (CBO) | CountClassCoupled | The Coupling Between Object Classes (CBO) measure for a class is a count of the number of other classes to which it is coupled. Class A is coupled to class B if class A uses a type, data, or member from class B. This metric is also referred to as Efferent Coupling (Ce). Any number of couplings to a given class counts as 1 towards the metric total Chidamber & Kemerer suggest that: 1) Excessive coupling between object classes is detrimental to modular design and prevents reuse. 2) Inter-object class couples should be kept to a minimum. 3) The higher the inter-object class coupling, the more rigorous testing needs to be. |
| Lack of Cohesion in Methods (LCOM) | PercentLackOfCohesion | 100% minus average cohesion for class data members. Calculates what percentage of class methods use a given class instance variable. To calculate, average percentages for all of that class'es instance variables and subtract from 100%. A lower percentage means higher cohesion between class data and methods. |