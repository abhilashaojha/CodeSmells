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
    L-->M(rules.JRip);
    L-->N(trees.J48);
    L-->O(Bayes.NaiveBayes);
    L-->P(trees.RandomForest);
 ```
## Selected Java Systems: 
<table> <th>System </th> <th>Source</th> <th>LOC (Lines of Code)</th> <th>NOP (Number of Parameter)</th> <th>NOC (Number of Children)</th> <th>NOM (Number of Methods)</th> <tr><td>Freemind-0.9.0 </td> <td>Qualitas Corpus</td>  <td>65,687</td>  <td>43</td> <td>849</td> <td>5788</td> </tr>     <tr><td>argouml-0.34</td> <td>Qualitas Corpus</td>  <td>284,934</td>  <td>125</td> <td>2361</td> <td>18,015</td> </tr>       <tr><td>Sunflow-0.07.2</td> <td>Qualitas Corpus</td>  <td>24,319</td>  <td>21</td> <td>191</td> <td>1447</td> </tr>         <tr><td>Retrofit</td> <td>Github Repository</td>  <td>6006</td>  <td>23</td> <td>151</td> <td>683</td> </tr>            <tr><td>Apache Ant-1.8.4</td> <td>Qualitas Corpus</td>  <td>119486</td>  <td>80</td> <td>1172</td> <td>13223</td> </tr>         <tr><td>ArtOfIllusion-2.8.1</td> <td>Qualitas Corpus</td>  <td>136,533</td>  <td>22</td> <td>799</td> <td> 688</td> </tr>        <tr><td>Mockito</td> <td>Github Repository</td>  <td>25758</td>  <td>103</td> <td>648</td> <td>3857</td> </tr>                     <tr><td>Fitjava-1.1</td> <td>Qualitas Corpus</td>  <td>2453</td>  <td>2</td> <td>60</td> <td>254</td> </tr>                    <tr><td>c-jdbc-2.0.2</td> <td>Qualitas Corpus</td>  <td>72408</td>  <td>101</td> <td>543</td> <td>5193</td> <tr>              <tr><td>Cobertura-1.9.4.1</td> <td>Qualitas Corpus</td>  <td>58,364</td>  <td>19</td> <td>107</td> <td>3309</td> </tr>               <tr><td>Castor-1.3.1</td> <td>Qualitas Corpus</td>  <td>213,479</td>  <td>149</td> <td>1542</td> <td>11,967</td> </tr>                <tr><td>ActionBarSherlock</td> <td>Github Repository</td>  <td>20108</td>  <td>24</td> <td>158</td> <td>2584</td> </tr>               <tr><td>Colt-1.2.0</td> <td>Qualitas Corpus</td>  <td>41872</td>  <td>25</td> <td>297</td> <td>3960</td> </tr>                <tr><td>Gnattproject-2.0.9</td> <td>Qualitas Corpus</td>  <td>58,718</td>  <td>54</td> <td>959</td> <td>5518</td> </tr>  </table>

## **1. Collection of Java Systems:**

Code Smells, on both Class and method level, were detected using iPlasma tool.The Four detected code smells are defined as follows:

* **Brain Class (BC):** Similar to God class, Brain Class refers to complex functionality of the system. It manifests itself as a long and complex class that becomes difficult to understand and maintain.

* **Schizofrenic Class (SC):** Schizofrenic Class code smell refers to a derived class that overrides behaviour of the base class and can be used as a template for objects whose behaviours are refined by the base classes.

* **Brain Method(BM):** Brain Methods are the code smells for concentrating a class's intelligence. It encapsulates a class's functionality in a single method. A method should avoid extremes in size. The issue with Brain Methods is that they are very extensive, making them difficult to understand and debug, as well as almost impossible to reuse.
* **Shotgun Surgery(SS):** It is a concept where appending one method or class require changes to be made in coupled methods or classes. Because of this, it's simple to overlook important method adjustments, which makes system maintenance tough.

For Class level code smells, all 14 projects are considered. The Code smell detected on Class Level are:
<table> <th>Java Project</th> <th>Brain Class</th> <th>Schizofrenic Class</th> <tr><td>Freemind-0.9.0</td> <td>2</td> <td>39</td></tr> <tr><td>Argouml-0.34</td> <td>11</td> <td>55</td> </tr> <tr><td>Sunflow-0.07.2</td> <td>5</td> <td>19</td> </tr>  <tr><td>Retrofit</td> <td>-</td> <td>17</td> </tr>      <tr><td>Apache-ant-1.8.4</td> <td>12</td> <td>117 </td> </tr>  <tr><td>ArtOfIllusion-2.8.1</td> <td>27</td> <td>44</td> </tr>   <tr><td>Mockito</td> <td>-</td> <td>140</td> </tr>   <tr><td>Fitjava-1.1 </td> <td>-</td> <td>8</td> </tr>   <tr><td>c-jdbc-2.0.2</td> <td>12</td> <td>44</td> </tr>   <tr><td>Cobertura-1.9.4.1</td> <td>1</td> <td>10</td> </tr> <tr><td>Castor-1.3.1</td> <td>24</td> <td>58</td> </tr> <tr><td>ActionBarSherlock</td> <td>-</td> <td>85</td> </tr> <tr><td>Colt-1.2.0 </td> <td>16</td> <td>4</td> </tr>   <tr><td>Gnattproject-2.0.9</td> <td>-</td> <td>56</td> </tr>    </table>

For method level code smells, only 4 projects were considered, mentioned below. The code smells detected on method level are: 

<table> <th>Java Project</th> <th>Brain Method</th> <th>Shotgun Surgery</th> <tr><td>Freemind-0.9.0</td> <td>34</td> <td>98</td></tr> <tr><td>Argouml-0.34</td> <td>136</td> <td>277</td> </tr> <tr><td>Sunflow-0.07.2</td> <td>39</td> <td>70</td> </tr>  <tr><td>Retrofit</td> <td>1</td> <td>1</td> </tr> </table>

## **2. Creation of Dataset:**
For each code smell type, a dataset has been created: two datasets for class-level smells (Brain Class and Schizofrenic Class) and two for method-level smells (Brain Method and Shotgun Surgery). In each dataset, each row represents class or method instances, and has one attribute for each metric. The labeled dataset at class level
contains 8,066 instances and 53 columns whereas that at method level contains 10,097 instances and 47 columns.

The dataset can be accessed here: [Datasets]

After the creation of the datasets, it was observed that some of the metric column contained >90% zeroes. Thus, cleaning was done on all the datasets. This reduced the dimension of the datasets in the following way:

<table> <th>Dataset</th>   <th>Dimension(rows,columns)</th>     <tr>  <td>brain_class.csv </td>  <td>(8026,47)</td> </tr>        <tr>  <td>schizophrenic_class.csv</td>  <td>(8026,47)</td> </tr>               <tr>  <td>brain_method.csv</td>  <td>(8872,45)</td> </tr>           <tr>  <td>shotgun_surgery.csv</td>  <td>(8803,44)</td> </tr>
</table>

## **3. Applying Machine Learning Algorithm to the dataset:**
Following Machine Learning algorithms were applied to the dataset:

* **J48** is an implementation of the C4.5 decision tree. This algorithm produces human understandable rules for the classification of new instances. The Weka implementation offers three different approaches to compute the decision tree, based on the types of pruning techniques: pruned, unpruned and reduced error pruning. In
the experimentation, pruned type was considered.

* **JRip** is an implementation of a propositional rule learner. It is able to produce simple propositional logic rules for the classification, which are understandable to humans and can be simply translated into logic programming.

* **Random Forest** is a classifier that builds many classification trees as a forest of random decision trees, each one using a specific subset of the input features. Each tree gives a classification (vote) and the algorithm chooses the classification having most votes among all the trees in the forest.

* **Naïve Bayes** is the simplest probabilistic classifier based on applying Bayes’ theorem. It makes strong assumptions on the input: the features are considered conditionally independent among each other.

## **RESULT OF EXPERIMENTATION**
Every algorithm was applied in different configurations to each dataset, by means of 10- fold cross validation, and the performances obtained on each fold were recorded. Given below are the tables with recorded values:

<table> <tr><th>Brain Class cross-validation results</th></tr> <tr><th>Classifier</th>   <th>Accuracy</th>   <th>F-measure</th>   <th>Area under ROC</th> </tr> <tr>  <td>JRip_BC</td> <td>99.9887 %</td>  <td>1.000</td>    <td>1.000</td>  </tr>     <tr>  <td>JRip_BC</td> <td>99.9887 %</td>  <td>1.000</td>    <td>1.000</td>  </tr>
</table>

|`Brain Class cross-validation results`|
|:--:|
|<table>    <th>Classifier</th>   <th>Accuracy</th>   <th>F-measure</th>   <th>Area under ROC</th>          <tr>  <td>JRip_BC</td> <td>99.9887 %</td>  <td>1.000</td>    <td>1.000</td>  </tr>     <tr>  <td>J48-Pruned_BC</td> <td>99.9662 %</td>  <td>1.000</td>    <td>0.997</td>  </tr>                <tr>  <td>Naïve Bayes_BC</td> <td>94.296 %</td>  <td>0.970</td>    <td>0.986</td>  </tr>      <tr>  <td>Random Forest_BC</td> <td>98.6924 %</td>  <td>0.993</td>    <td>1.000</td>  </tr>       </table>|

