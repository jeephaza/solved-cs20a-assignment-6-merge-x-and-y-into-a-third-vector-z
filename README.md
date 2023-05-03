Download Link: https://assignmentchef.com/product/solved-cs20a-assignment-6-merge-x-and-y-into-a-third-vector-z
<br>
<strong>Problem 1: </strong>

Suppose you have two vector of integers x and y, each of which have <strong>N</strong> randomly distributed but distinct values.  We want to merge x and y into a third vector z such that z has all the integers of x and y, additionally z should not have any duplicate values.  For this problem we are not concerned with ordering in any of these vectors.

<ol>

 <li>Here is one algorithm. What is the Big-O of this algorithm?</li>

</ol>

void merge1(const vector&lt;int&gt;&amp; x, const vector&lt;int&gt;&amp; y, vector&lt;int&gt;&amp; z) {

z.clear();

z.reserve(x.size() + y.size());

for (int i = 0; i &lt; x.size(); ++i)         z.push_back(x[i]);

for (int j = 0; j &lt; y.size(); ++j) {         bool duplicate = false;        for (int i = 0; i &lt; x.size(); ++i) {

if (y[j] == x[i]) {

duplicate = true;

break;

}

}

if (!duplicate)

z.push_back(y[j]);

}

}

<ol>

 <li>Here is another algorithm that uses a sorting function, assume that the sort function is implemented as quicksort. What is this algorithm’s Big-O?</li>

</ol>

void merge2(const vector&lt;int&gt;&amp; x, const vector&lt;int&gt;&amp; y, vector&lt;int&gt;&amp; z) {

z.clear();

z.reserve(x.size() + y.size());

for (int i = 0; i &lt; x.size(); i++)         z.push_back(x[i]);

for (int j = 0; j &lt; y.size(); j++)         z.push_back(y[j]);

sort(z.begin(), z.end());

int last = 0;

for (int k = 1; k &lt; z.size(); k++) {

cout &lt;&lt; “—————–” &lt;&lt; endl;    print(z);

if (z[last] != z[k]) {

last++;

z[last] = z[k];

}

print(z);

}

z.resize(last + 1);

}

<ol>

 <li>Which algorithm performs better given the provided description of inputs?</li>

 <li>Suppose the input vectors are:</li>

</ol>

vector&lt;int&gt; x{1,2,3,4,5,6};

vector&lt;int&gt; y{7,8,9,10,11,12};

How will that change your analysis done in the previous parts?

<strong>Problem 2: </strong>

Suppose we are working with a general tree structure where each Node can have any number of children.  A Node is defined as:

struct Node {

int val;

vector&lt;Node *&gt; children;

};

<ol>

 <li>Write a recursive function that counts the number of Nodes in any (sub)tree passed into this function, including the one being passed into the function:</li>

</ol>

int nodeCount(Node *node) {




<ol>

 <li>Write a function that returns the number of edges in a tree using the function you implemented above:</li>

</ol>

int edgeCoun(Node *node) {

<ol>

 <li>Write a recursive function that counts the number of leaves that are in a given tree. Note that a leaf is a node with zero children.</li>

</ol>

int leafCount(Node *node) {

<strong>Problem 3: </strong>

Consider the <u>binary tree</u> on the right:

<ol>

 <li>What is the pre-order, post-order, in-order traversal for this tree?</li>

 <li>What can you always say about the root node with a pre-order traversal? Post-order?</li>

 <li>If given an in-order traversal and you are told which value corresponds to the root node, what can you say about the values that appear to the left of the root node’s value with regards to their placement in the tree? Values that appear to the right?</li>

 <li>It is possible to construct a unique binary tree when given both its pre-order and in-order traversals</li>

</ol>

(The same is true for post/in, but not pre/post).  Given the following traversals, draw the binary tree:

<strong> </strong>

<u>Pre-order</u>:  A B D E F C G H J L K

<u>In-order</u>:      D B F E A G C L J H K

<strong>Problem 4: </strong>

<ol>

 <li>How many nodes does a <u>full binary tree</u> of height 2 have? (height being the number of edges from the root to the deepest leaf)</li>

 <li>Draw a <u>binary tree</u> of height 2 whose post-order traversal is S, M, B, R, T, E, I.</li>

 <li>What is the level-order traversal of the tree you created above?</li>

 <li>Draw a <u>binary tree</u> of height 2 whose pre-order traversal is S, M, B, R, T, E, I.</li>

 <li>What is the in-order traversal of the tree you created above?</li>

</ol>

<strong>Problem 5: </strong>

<ol start="8">

 <li>Draw a <u>complete binary search tree</u> with height 2 whose in-order traversal is 2,3,4,5,6,8.</li>

 <li>What is the post-order traversal of this tree</li>

 <li>What is the pre-order traversal of this tree?</li>

 <li><strong>Problem 6:</strong></li>

</ol>

Consider the following <u>open hash table</u> implementation.

const int  HASH_SIZE = 10;

class OpenHashTable { public:

int hashFunc(int x) {          return (x * 2) % HASH_SIZE;

}




void insert(int key) {




int index = hashFunc(key);

hash_array[index].push_back(key);




}

private:

list&lt;int&gt; hash_array[HASH_SIZE];




};

<ol>

 <li>Draw the state of hash_array to the right after the following calls.  The first two elements are drawn in there for you.</li>

</ol>

OpenHashTable oh;  oh.insert(7);  oh.insert(1);  oh.insert(23);  oh.insert(14);  oh.insert(19);  oh.insert(53);  oh.insert(37);  oh.insert(83);

<ol>

 <li>Is hashFunc() a good hash function? Why or why not?</li>

 <li>Using the current state of the hash table, what is the load factor and average number of checks for this hash table?</li>

 <li>How many checks on average would a <u>closed hash table using linear probing</u> have using the same load factor?</li>

 <li>For original open hash table, how much bigger would I need to make this hash table if I wanted an average number of checks being roughly 1.05?</li>

</ol>

<strong>Problem 7:</strong>

Consider the following array-based <u>maxheap</u> that has two operations, extractMax() and insert(int num).

<ol>

 <li>How does the <u>maxheap</u> look after calling extractMax()?</li>

 <li>How does it look after calling insert(12)?</li>

 <li>Draw the equivalent complete binary tree of this <u>maxheap</u>.</li>

</ol>

<strong>Problem 8:</strong>

<ol>

 <li>Suppose we have a <u>maxheap</u> which can be visualized with a <u>ternary tree</u> (up to three children). If we wanted to convert this to an array based <u>maxheap</u>, how would we find the left, middle, right child for any particular node? The parent for any particular node?</li>

 <li>What is the complexity of insertion into this maxheap? Complexity of extraction?</li>

</ol>

<strong>Problem 9: </strong>

You are hired to design a website called<em> brotionary.com</em>, a <em>dictionary.com</em> variant. You are given a list of <strong>N</strong> dictionary words (and their definitions) in a text file, and would like to preprocess it, such that you can readily provide information to users who visit your website and look up words. Assume that your dictionary is not going to be updated once it is preprocessed. We still want your system to “scale” — that is, it should be able to efficiently take care of <strong>a lot of queries</strong> that may come in.




Assume a Word structure like the following is used to store each word and definition.




struct Word {

string word;

string definition;

};

<ol>

 <li>First of all, the users should be able to look up words. Which of the following options would you take, and why?</li>

</ol>

<u>Option A</u>: Store the Words in a <u>binary search tree</u>. <u>Option B</u>: Store the words in a <u>hash table</u>.

<ol>

 <li>You want to add functionality that prints words and their definitions within a certain range of <strong>P</strong></li>

</ol>

e.g all the words between and including aardvark and awkward.  Which of the following options would you take, and why?




<u>Option A</u>: Add a sorted <u>singly linked list</u> with pointers to Words in the structure used in part a. Each time a range [x:y] is specified, we search for word x in the list, and then traverse the list to print each word, until we hit word y.

<u>Option B</u>: Add a sorted <u>vector</u> with pointers to Words in the structure used in part a. Each time a range [x:y] is specified, we search word x in the vector, and then traverse the vector to print each word, until we hit word y.

Page

<ol>

 <li>In the right corner of the website, you want to display “<strong>K</strong> most popular words”, where <strong>K</strong> is some integer, which are determined by queries that were received in the past hour, and is updated every hour. Assume queries are made on <strong>M</strong> distinct words, where <strong>M</strong> &gt;&gt;<strong>K</strong>. Which option would you take, and why?</li>

</ol>

<u>Option A</u>: In the beginning of every hour, create a <u>hash table</u> (initially empty) that stores (word, count)pairs. Each time a query for a word x comes in, look up x in the hash table (or add a new one if one does not exist), and increase the count for x. At the end of the hour, iterate through all (word, count)-pairs in the <u>hash table</u> and store them in a <u>maxheap</u>, using their counts as the keys. Then extract <strong>K</strong> words from the heap.

<u>Option B</u>: In the beginning of every hour, create a <u>vector</u> (initially empty) that stores (word, count)pairs. Each time a query for a word x comes in, look up x in the vector (or add a new one if one does not exist), and increase the count for x. At the end of the hour, sort the pairs in the vector in the decreasing order of their counts, and print the first <strong>K</strong> words

Page