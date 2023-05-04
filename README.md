Download Link: https://assignmentchef.com/product/solved-csci-561-foundations-of-artificial-intelligence-homework-3
<br>












<h1>Project Description</h1>




RipeApe pharmacy is developing a self-service automated system to alert customers about potential drug interactions for both prescription and over-the-counter drugs. Many medications should not be taken together or should not be taken if a patient has certain symptoms and allergies. Evaluating all the criteria for whether a patient can take a particular medication requires the patient’s medical history and expert knowledge from a health care provider. The system, however, can provide an instant guideline to keep patients informed and minimize the risks.




You are assigned by RipeApe to develop a beta version of the system using the first order logic inference. Patient history and drug compatibility data will be encoded as first order logic clauses in the knowledge base. The program takes a query of new drug list and provide a logical conclusion whether to issue a warning.




You will use <strong>first-order logic resolution</strong> to solve this problem.




<strong><u>Format for input.txt</u> </strong>

<strong> </strong>

&lt;N = NUMBER OF QUERIES&gt;

&lt;QUERY 1&gt;

…

&lt;QUERY N&gt;

&lt;K = NUMBER OF GIVEN SENTENCES IN THE KNOWLEDGE BASE&gt;

&lt;SENTENCE 1&gt;

…

&lt;SENTENCE K&gt;




The first line contains an integer <em>N</em> specifying the number of queries. The following <em>N</em> lines contain one query per line. The line after the last query contains an integer <em>K</em> specifying the number of sentences in the knowledge base. The remaining <em>K</em> lines contain the sentences in the knowledge base, one sentence per line.




<strong><em>Query format:</em></strong> Each query will be a single literal of the form Predicate(Constant_Arguments) or

~Predicate(Constant_Arguments) and will not contain any variables. Each predicate will have between 1 and 25 constant arguments. Two or more arguments will be separated by commas.




<strong><em>KB format:</em></strong> Each sentence in the knowledge base is written in one of the following forms:

<ul>

 <li>An <em>implication</em> of the form <em>p<sub>1</sub> </em>∧<em> p<sub>2</sub> </em>∧<em> … </em>∧<em> p<sub>m</sub> </em>⇒<em> q, </em>where its premise is a conjunction of literals and its conclusion is a single literal. Remember that a literal is an atomic sentence or a negated atomic sentence.</li>

 <li>A single literal: <em>q</em> or ~<em>q</em></li>

</ul>




Note:

<ol>

 <li><sub>&amp;</sub> denotes the <em>conjunction</em></li>

 <li><sub>|</sub> denotes the <em>disjunction</em> It will not appear in the queries nor in the KB given as input. But you will likely need it to create your proofs.</li>

 <li><sub>=&gt;</sub> denotes the <em>implication</em></li>

 <li><sub>~</sub> denotes the <em>negation</em></li>

 <li>No other operators besides <sub>&amp;, =&gt;</sub>, and <sub>~</sub> are used in the knowledge base.</li>

 <li>There will be no parentheses in the KB except as used to denote arguments of predicates.</li>

 <li>Variables are denoted by a single lowercase letter.</li>

 <li>All predicates (such as <sub>HighBP</sub>) and constants (such as <sub>Alice</sub>) are case sensitive alphabetical strings that begin with uppercase letters.</li>

 <li>Each predicate takes at least one argument. Predicates will take at most 25 arguments. A given predicate name will not appear with different number of arguments.</li>

 <li>There will be at most 10 queries and 100 sentences in the knowledge base.</li>

 <li>See the sample input below for spacing patterns.</li>

 <li>You can assume that the input format is exactly as it is described.</li>

 <li>There will be no syntax errors in the given input.</li>

 <li>The KB will be true (i.e., will not contain contradictions).</li>

</ol>




<strong><u>Format for output.txt:</u> </strong>




For each query, determine if that query can be inferred from the knowledge base or not, one query per line:




&lt;ANSWER 1&gt;

…

&lt;ANSWER N&gt;




Each answer should be either TRUE if you can prove that the corresponding query sentence is true given the knowledge base, or FALSE if you cannot.

<strong> </strong>

<strong><u>Notes and hints:</u> </strong>




<ul>

 <li>Please name your program “<strong>xxx</strong>” where ‘xxx’ is the extension for the programming language you choose. (“<strong>py</strong>” for python, “<strong>cpp</strong>” for C++, and “<strong>java</strong>” for Java). If you are using C++11, then the name of your file should be “homework11.cpp” and if you are using python3 then the name of your file should be “homework3.py”.</li>

 <li>If you decide that the given statement can be inferred from the knowledge base, every variable in each sentence used in the proving process should be unified with a Constant (i.e., unify variables to constants before you trigger a step of resolution).</li>

 <li>All variables are assumed to be universally quantified. There is no existential quantifier in this homework. There is no need for Skolem functions or Skolem constants.</li>

 <li>Operator priorities apply (negation has higher priority than conjunction). There will be no parentheses in the sentences, other than around arguments of predicates.</li>

 <li>The knowledge base is consistent.</li>

 <li>If you run into a loop and there is no alternative path you can try, report FALSE. An example for this would be having two rules <strong><em>(1)</em></strong> A(x) =&gt; B(x) and <strong><em>(2)</em></strong> B(x) =&gt; A(x) and wanting to prove A(John). In this case your program should report FALSE.</li>

 <li>Note that the KB is not in Horn form because we allow more than one positive literal. So you indeed must use resolution and cannot use generalized Modus Ponens.</li>

</ul>







<strong><u>Example 1:</u> </strong>




For this input.txt:




1

Take(Alice,NSAIDs)

2

Take(x,Warfarin) =&gt; ~Take(x,NSAIDs) Take(Alice,Warfarin)







your output.txt should be:







FALSE

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong><u>Example 2:</u> </strong>

<strong> </strong>

For this input.txt:




2

Alert(Bob,NSAIDs)

Alert(Bob,VitC)

5

Take(x,Warfarin) =&gt; ~Take(x,NSAIDs)

HighBP(x) =&gt; Alert(x,NSAIDs)

Take(Bob,Antacids)

Take(Bob,VitA)

HighBP(Bob)







your output.txt should be:







TRUE

FALSE










<strong><u>Example 3:</u> </strong>

<strong> </strong>

For this input.txt:




3

Alert(Alice,VitE)

Alert(Bob,VitE)

Alert(John,VitE)

9

Migraine(x) &amp; HighBP(x) =&gt; Take(x,Timolol)

Take(x,Warfarin) &amp; Take(x,Timolol) =&gt; Alert(x,VitE)

Migraine(Alice)

Migraine(Bob)

HighBP(Bob)

OldAge(John)

HighBP(John)

Take(John,Timolol)

Take(Bob,Warfarin)







your output.txt should be:







FALSE

TRUE

FALSE








