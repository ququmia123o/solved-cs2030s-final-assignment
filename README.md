Download Link: https://assignmentchef.com/product/solved-cs2030s-final-assignment
<br>
<strong>Question 1: Object-Oriented Design  </strong>(a) (Study the following class A.

class A { private A other;

void set(A other) { this.other = other;

}

A get() {

return this.other;

}

}

Without modifying class A, write a series of jshell instructions to generate two instances a1 and a2 both of type A, where the other property a1 refers to a2, and vice versa.

Write further jshell instructions to test that the assignment of the other property is valid and correct. Write your answer in the file: oop-a.jsh

<ul>

 <li> Suppose we would like to include more classes B, C, etc. that are similar to class A, i.e. having an other property that can refer to any object of type A, B, C, etc.</li>

</ul>

Come up with an appropriate design and write the complete implementation. For simplicity, you may assume instances of class A and B currently, but your design should be readily extensible for other classes. There is no need to write jshell tests; the tests in part (a) must work here also. Write your answer in the file: oop-b.java

<ul>

 <li>Notice that the implementation of part(a) is mutable. Specifically the other property can be mutated after the object is created. Re-implement the solution of part (b) such that objects of classes A, B, C, etc. are now immutable. You may assume that the other property will always refer to some other object (i.e. not itself).</li>

</ul>

Write your answer in the file: oop-c.java

<ul>

 <li> Write a Main class with a main method to demonstrate how a chain of objects is created such that the following</li>

</ul>

System.out.println(a); // a references an instance of type A

System.out.println(a.get());

System.out.println(a.get().get());

System.out.println(a.get().get().get());

System.out.println(a.get().get().get().get()); System.out.println(a.get().get().get().get().get()); would result in the output (addresses of the objects might differ), <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="df9e9febbdeeedeeefbaba">[email protected]</a>

<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="e7a6a7d48483d686d581d6">[email protected]</a>

<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="743634404d4043424c4046">[email protected]</a>

<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="ffbdbfcdc89ccec8cf99cf">[email protected]</a>

<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="6928295d0b585b58590c0c">[email protected]</a>

<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="cd8c8dfeaea9fcacffabfc">[email protected]</a>

Write your answer in the file: oop-d.java. There is no need to reproduce the output statements.

<strong>Question 2: Generics  </strong>Study the following replace method.

void replace(List&lt;Integer&gt; src, List&lt;Integer&gt; dst) { if (src.size() == dst.size()) { for (int i = 0; i &lt; src.size(); i++) { if (src.get(i) &gt; dst.get(i)) { dst.set(i, src.get(i));

}

}

} }

jshell&gt; List&lt;Integer&gt; destination = new ArrayList&lt;&gt;(List.of(1,2,3)) destination ==&gt; [1, 2, 3] jshell&gt; replace(new ArrayList&lt;&gt;(List.of(9,9,9)), destination)

jshell&gt; destination destination ==&gt; [9, 9, 9]

Notice that the destination list is replaced by elements of the source list since the corresponding element in the source list is larger.

<ul>

 <li>Rewrite the replace method so that it works on lists of any type T. The replace method should also take as input the criteria for replacement.</li>

</ul>

Write your answer in the file: generics-a.jsh

<ul>

 <li>Construct a test such that the types of the source list, destination list andtype of criteria are different, but still related by some super-class or sub-class relationship. Express an appropriate criteria such that all elements of the destination are always replaced by the source.</li>

</ul>

Write your answer in the file: generics-b.jsh

<strong>Question 3: Lambda </strong>Refer to the class Foo below.

class Foo { static int y = 1;

Runnable bar() { int x = 1;

Runnable r1 = () -&gt; System.out.println(x);

<ul>

 <li>= x + 1;return r1;</li>

</ul>

}

Runnable baz() {

Runnable r2 = () -&gt; System.out.println(y);

<ul>

 <li>= y + 1;return r2;</li>

</ul>

}

}

Explain why one of the lambdas compiles without error, while the other does not. Write your answer in the file: lambda.txt

<strong>Question 4: Functor (6 marks)</strong>

Your classmate I.M. Smart has created a Box class, and claims that it is a functor.

public class Box { private String value = “”;

private Box(String s) { value = new StringBuffer(s).reverse().toString();

}

public static Box of(String input) { return new Box(Objects.requireNonNull(input));

}

public Box map(Function&lt;String, String&gt; f) { return new Box(f.apply(this.value));

}

@Override public String toString() { return value;

}

}

<ul>

 <li>(1 mark) What is the output of of(“the Quick bROwn fox”).toString() ?</li>

</ul>

Write your answer in the file: functor-a.txt

<ul>

 <li>(2 marks) What could x be if</li>

</ul>

Box.of(x).map(s-&gt; s.repeat(2)).toString(); produces HelloHello

Write your answer in the file: functor-b.txt

<ul>

 <li>(3 marks) Does Box obey the functor laws? Give a concrete example.</li>

</ul>

Write your answer in the file: functor-c.txt

<strong>Question 5: Lazy Evaluation (10 marks)</strong>

Refer to the code in LazyList.java, provided for you in this exam folder.

<ul>

 <li>(2 marks) After the following code is executed, how many times is filter eagerly called? (Just state the number; no explanation needed.)</li>

</ul>

LazyList.intRange(101, 200).filter(n-&gt; n%2==0);

Write your answer in the file: lazy-a.txt

<ul>

 <li>(2 marks) After the following code is executed, how many times is map eagerly called?</li>

</ul>

(Just state the number; no explanation needed.)

LazyList.intRange(2, 100)

.map(n-&gt; 2*n)

.filter(n-&gt; n &gt; 11);

Write your answer in the file: lazy-b.txt

<ul>

 <li>(2 marks) Counting the number of items in a LazyList is a reduction operation. Write an instance method count() that returns the number of items in this list by calling reduce with suitable arguments. Do not use explicit loops: eg. for, while, or recursion; and do not use Java stream. Instead, use map, flatMap or filter, as appropriate. You may assume that the list is finite.</li>

</ul>

Write your answer in the file: lazy-c.java

<ul>

 <li>(4 marks) Let’s rewrite the permute function of Recitation 8, so that it can permute objects of type T, and handle the case <em>r </em>= 0:</li>

</ul>

&lt;T&gt; LazyList&lt;LazyList&lt;T&gt;&gt; permute(LazyList&lt;T&gt; LL, int r) { if (r == 0)

return LLmake(LazyList.makeEmpty(), LazyList.makeEmpty());

else if (LL.isEmpty()) return LazyList.makeEmpty();

else return LL.flatmap(x -&gt; permute(remove(LL, x), r – 1)

.map(y -&gt; LLmake(x,y)));

}

&lt;T&gt; LazyList&lt;T&gt; remove(LazyList&lt;T&gt; LL, T n) { return LL.filter(x-&gt; !x.equals(n));

}

You would have learned from mathematics that an <em>r</em><strong>-Combination </strong>is an <em>r</em>-Permutation where order does not matter. That is, (1, 2, 3) is the same 3-Combination as (1, 3, 2), even though they are different 3-Permutations.

Complete the code below to implement the choose function that returns a LazyList of <em>r</em>−Combinations (each of which is a length-<em>r </em>LazyList), when given a LazyList of <em>n </em>objects as input. You may assume that the input is finite.

<em>Hint: </em>Observe that you can group all the <em>r</em>-Combinations into two groups: those that use the first list item, and those that do not. Recursively generate these two groups, then concat them.

&lt;T&gt; LazyList&lt;LazyList&lt;T&gt;&gt; choose(LazyList&lt;T&gt; LL, int r) { if (r == 0)

return LLmake(LazyList.makeEmpty(), LazyList.makeEmpty());

else if (LL.isEmpty()) return LazyList.makeEmpty();

else

//insert your code here

}

Write your answer in the file: lazy-d.java

<strong>Question 6: Streams (8 marks)</strong>

<ul>

 <li>(1 mark) The following program fragment is run in jshell.</li>

</ul>

int s = 0;

IntStream.range(1, 100).boxed().forEach(x -&gt; s = s + x); s;

What is the purpose of the above program fragment? State <strong>what it does</strong>, and not how it is done.

Write your answer in the file: stream-a.txt

<ul>

 <li>(2 marks) Comment on the way the stream was constructed to achieve the purpose ofpart (a). Rewrite the solution if necessary. Write your answer in the file: stream-b.jsh</li>

 <li>(1 mark) Suppose we parallelize the stream construct in part (a) by including parallel() just before the forEach Would it be correct? Explain. Write your answer in the file: stream-c.txt</li>

 <li>(2 marks) Complete the following stream pipeline to count the total number of lettersin a given list of words. If there are no words in the list, count will return 0.</li>

</ul>

int count(List&lt;String&gt; words) { return words.stream()

.map(

.reduce(

}

Write your answer in the file: stream-d.jsh

<ul>

 <li>(2 marks) Do the same as in part (d), but this time with only one reduce</li>

</ul>

int count(List&lt;String&gt; words) { return words.stream()

.reduce(

}

Write your answer in the file: stream-e.jsh