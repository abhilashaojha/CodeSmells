# **Analysis of Code Smells at Class and Method Level**
> This is my fourth semester Masters dissertation paper associated with **Banaras Hindu University**.
## What are Code Smells?
Code smells are considered to be a bad symptom of the code.They are neither defects in the code nor obstacles to the code's execution. They simply indicate a design flaw and may raise the likelihood of errors and program failure in the future.

As Martin Fowler (1999) puts it, 
> "Surface indications that usually correspond to deeper problems in the software system."

## When are code smells identified?
Code smells is identified when improper programming methods lead to flaws in the design and implementation of the code, which can wreak havoc on software development, maintenance, and evolution. 

* Manual inspection of the systems is slow and ineffective. Thus, several tools were developed for the detection of the same. 

**Available tools are:**
* `PMD`, `iPlasma`, `Jdeodorant` and `Stench Blossom`. 
* These tools are quite helpful in detecting problematic code smells and enhancing the software project's integrity and manageability.

Here, 

[iPlasma](https://github.com/abhilashaojha/CodeSmells/blob/main/iPlasma6.zip) tool has been used to create the dataset on Code Smell. 

Machine learning methods are implemented using the [Weka](https://sourceforge.net/projects/weka/) software, which is also used to verify the algorithm's accuracy.

## Workflow of the Paper:
***

```mermaid
graph TD;
    A[Java System Collections]-->B(11 heterogenous java systems from Qualitas Corpus);
    A[Java System Collections]-->C(3 heterogenous java software systems from Github Repository);
    B-->D;
    C-->D;
    D[Code smell detection and extraction of metrics with iPlasma]-->E(Class Level);
    D[Code smell detection and extraction of metrics with iPlasma]-->F(Method level);
    E-->G((Brain CLass));
    E-->H((Schizofrenic Class));
    F-->I((Brain Method));
    F-->J((Shotgun Surgery));
    G-->K[Preprocessing and Cleaning of the Dataset];
    H-->K;
    I-->K;
    J-->K;
    K-->L[Machine Learning Algorithm utilising Code Metrics];
    K-->M(rules.JRip);
    K-->N(trees.J48);
    K-->O(Bayes.NaiveBayes);
    K-->P(trees.RandomForest);
 ```

