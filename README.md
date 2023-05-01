Download Link: https://assignmentchef.com/product/solved-cis2500-assignment-4-linked-lists-recursion-and-adts
<br>
Question 1a: Advanced Linked Lists




[<em>bonus 10% for Q1 – doubly linked lists</em>]

typedef struct NODE {                 typedef struct NODE {         value_typekey_type key value; ;              <strong>or</strong>             value_typekey_type key; value;

struct NODE * next;                     struct NODE * next;     struct NODE * sort;                     struct NODE * sort;

} Node;               struct NODE * prev;            struct NODE * prev_sorted;

} Node;

In this linked list:

<ul>

 <li>The datatype for the value being stored is called value_type</li>

 <li>The datatype for the key being stored is called key_type</li>

 <li>As in lab 4, next links to the node in the order it was added to the list (either at the head or the tail) o This will be referred to as <em>insertion</em> <em>order</em></li>

 <li>Si<span style="text-decoration: line-through;">milar </span>to<span style="text-decoration: line-through;"> la</span>b 4, sort links to the node where the key is greater or equal to its key o e. the list is kept in ascending order by key o This will be referred to as <em>key sort order</em>  o Note: unlike lab 4, there is only one key</li>

</ul>










<h1>Create a Sorted List abstract data type</h1>

<ul>

 <li>Has two heads (head <em>for insertion order</em>, head_sort <em>for key sort order</em>)</li>

 <li>Has two tails (tail <em>for insertion order</em>, tail_sort <em>for key sort order</em>)</li>

 <li>Has an int field called size that stored the node count (the number of elements in the list)</li>

 <li>The datatype should be called Sorted_List</li>

</ul>

<em>      Note:  technically you will be implementing only be a subset of the Sorted List ADT                     as you will not be asked to implement all functions of the full ADT </em>

<strong>             </strong>

<h1>Functions to be implemented</h1>

<em>All functions, except where noted, return SUCCESS if the function can complete or FAIL if not </em>

<ul>

 <li>int size (Sorted_List *)

  <ul>

   <li>returns the number of nodes in the list (not SUCCESS/FAIL as the function cannot fail)</li>

  </ul></li>

 <li>int push ( Sorted_List *, value_type , key_type )

  <ul>

   <li>add the node to the head of the list</li>

   <li>the node must also be inserted in <strong>ascending</strong> sort order by key, using the sort link</li>

  </ul></li>

 <li>int append ( Sorted_List * , value_type , key_type ) o similar to push, except the node gets added to tail</li>

 <li>int remove_first ( Sorted_List * , value_type * , key_type *) o removes the node from the head of the list

  <ul>

   <li>returns the value and key of the removed node through the parameter values</li>

  </ul></li>

</ul>

(and frees the node) o returns SUCCESS (alternatively you can change the signature to return void) o remember to update the sort order links

<ul>

 <li>if not using doubly linked lists, you will need to find the previous sorted node to change its sort order link</li>

</ul>

<ul>

 <li>int remove_last ( Sorted_List * , value_type * , key_type * )

  <ul>

   <li>similar to remove_first, except it removes the node from the tail</li>

  </ul></li>

 <li>int remove_smallest_key ( Sorted_List * , value_type * , key_type * ) o removes the node with the smallest key

  <ul>

   <li>returns the value and key of the removed node (and frees the node) o remember to update the insertion order links

    <ul>

     <li>if not using doubly linked lists, you will need to find the previous insert order node to change its insertion order link</li>

    </ul></li>

   <li>int remove_largest_key ( Sorted_List * , value_type * , key_type * )

    <ul>

     <li>similar to remove_smallest_key, except it removes the node with the largest key</li>

    </ul></li>

   <li>void empty_list ( Sorted_List *)

    <ul>

     <li>empties the contents of the list</li>

     <li>remember to free the memory of the contents</li>

    </ul></li>

   <li>void destroy_list ( Sorted_List *)

    <ul>

     <li>empties the contents of the list, as well as freeing the list itself</li>

    </ul></li>

  </ul></li>

</ul>




<strong>             </strong>

<h1>To test the Sorted List ADT</h1>

<em>Write two programs called   </em>a4q1a_char.c<em>   and   </em>a4q1a_int.c

<ul>

 <li>Data types used o c

  <ul>

   <li>has its value_type  datatype set equal to  int</li>

   <li>has it key_type  datatype set equal to  double o c<em>   </em></li>

   <li>has its value_type  datatype set equal to char[80]</li>

  </ul></li>

 <li>e. it can take strings up to 79 characters in length</li>

 <li>has its key_type datatype set equal to  int</li>

 <li>its value is set equal to the length of the string</li>

 <li>Both programs read in a text file that contains a series of commands, one per line</li>

</ul>

(i.e each ending with a newline) o The name of the text file should be entered as a command line argument

<ul>

 <li>If there is no file name, read from stdin</li>

 <li>this can use IO redirect, i.e. a4q1a_int &lt; filename.txt</li>

 <li>If using keyboard input, exit using ^d</li>

 <li>All commands are echoed to stdout, followed by a colon :, o After that the results of the command follows,</li>

 <li>usually on the same line following 11 – strlen(cmd name) spaces   or on the next line when noted</li>

</ul>

<em>        Note:  Silent commands do not have the colon : after the command,                           but rather after the command name </em>

<ul>

 <li>Remember to free the sorted list at the end of the program (use destroy_list)</li>

</ul>

<em> </em>

General Note: The two programs should be almost identical, with the following differences o The file input will be slightly different depending on the data type and nature of the input data o Your will have to write similar, but not identical void print_list_all ( Sorted_List * )  and void print_list_sort ( Sorted_List * ) functions

<ul>

 <li>These functions print out the lists according to their respective sort orders</li>

 <li>See the report commands section below for details</li>

</ul>

(the print_all and print_sort commands)

o You will have to have your make file recompile all files that mention or use value_type and key_type variables or Sort_List structs when compiling the two programs

<ul>

 <li>To do this you will need to use condition compilation (see Week1 lecture notes)</li>

 <li>In specific, use #ifdef CHAR to compile using the char[80] typedef definition of value_type</li>

</ul>

and #ifdef INT to compile using the int typedef definition of value_type

<ul>

 <li>g. if you stored all your Sort_List ADT functions in a single file called sort_list.c Then for a4q1a_char.c you could have in your make file a command like</li>

</ul>




gcc  -Wall -ansi -DCHAR -c sort_list.c

<em> </em>

<em> </em>

<h1>List of Commands</h1>

<strong><em>Silent Commands (modifies the list but does not print anything other than the command itself) </em></strong>

<ul>

 <li>a = append</li>

</ul>

o a4q1a_int.c<em>   </em>

<ul>

 <li>input line: a   key value</li>

</ul>

<em>note: there can be any number of spaces in the input been the command and args, or between args</em>

<ul>

 <li>example</li>

</ul>

<ul>

 <li><em>commands, as stored in the input file</em></li>

</ul>

a   3.27   1427   a   0.94   984

a   7.21   346

<ul>

 <li><em>output</em>(11 – 1 spaces after the colon)</li>

</ul>

a:          3.27  1427   a:          0.94  984          a:          7.21  346

<ul>

 <li>c

  <ul>

   <li>input line: a   value</li>

   <li>example</li>

   <li><em>commands, as stored in the input file</em></li>

  </ul></li>

</ul>

a   The sun did not shine.   a   It was too wet to play.  a   So we sat in the house  a   All that cold, cold, wet day.

<em>          Note: skip the white space between the command ‘a’ and the input string </em>

<ul>

 <li>The key values for the above are 22, 23, 22, 29</li>

</ul>

<ul>

 <li>g. strlen(“The sun did not shine.”) == 22

  <ul>

   <li><em>output</em> (11 – 1 spaces after the colon)</li>

  </ul></li>

</ul>

a:          The sun did not shine.  a:          It was too wet to play.  a:          So we sat in the house  a:          All that cold, cold, wet day.

<ul>

 <li>p = push                   o same as a except it pushes instead of appends the key/value pair onto the list</li>

</ul>

<strong><em>Verbose Commands (modifies the list and then reports to stdout) </em></strong>

<ul>

 <li>rem_first = remove first node of the list by insertion order o also prints the element’s key-value pair, with two spaces between the key and the value</li>

</ul>

<ul>

 <li>Example for c assuming the first list element key is 2.465 and value is 212 rem_first: 2.465  212</li>

 <li>Note the two spaces after rem_first: “rem_first” is 9 characters in length,  so the number of spaces following should be  11 – 9 = 2</li>

 <li>If the list is empty, remove will fail. It should print then print the following rem_first: Nothing to remove</li>

 <li>rem_last = remove last node of the list by insertion order and print the element’s key-value pair</li>

 <li>rem_small = remove the node with the smallest key and print the element’s key-value pair rem_large = remove the node with the largest key and print the element’s key-value pair</li>

 <li>empty = empty the list o the output of this command should be</li>

</ul>

empty:      size = 0

<strong><em>Report Commands (prints information, but does not modify the list) </em></strong>

<ul>

 <li>size = size of sorted linked list</li>

</ul>

o if there are 21 nodes in the list it prints size:       List size = 21

<ul>

 <li>print_all = print list in insertion order o The type of order is printed on the same line as the command o The list starts printing on the next line, one element per line</li>

</ul>

o Each element is prefaced by 5 spaces, then the key, then 2 spaces, then the value o Example using the input from the append examples

<ul>

 <li>a4q1a_int.c print_all: Insertion Order</li>

</ul>

3.27  1427

0.94  984

7.21  346

<ul>

 <li>a4q1a_char.c print_all:  Insertion Order<em>  </em>

  <ul>

   <li>The sun did not shine.</li>

   <li>It was too wet to play.</li>

  </ul></li>

</ul>

22  So we sat in the house                 29  All that cold, cold, wet day.




<ul>

 <li>print_sort = print list in key sort order o The output is the same as with print_all except the order of the lines are in key sort order and the command line will read Key Sort Order</li>

</ul>

o Example using the input from the append examples

<ul>

 <li>a4q1a_int.c print_sort: Key Sort Order</li>

</ul>

0.94  984

3.27  1427

7.21  346

<ul>

 <li>a4q1a_char.c</li>

</ul>

print_sort: Key Sort Order<em>  </em>

22  The sun did not shine.

<ul>

 <li>So we sat in the house</li>

 <li>It was too wet to play.</li>

</ul>

29  All that cold, cold, wet day.







The assignment continues with Question 1b Function Pointers  to be released by March 26

<em>the relevant lecture notes for Q1b, presented the last week  of face-to-face classes, have now been posted </em>




Question 1b: List ADT and Function Pointers

Using the same data type Sorted_List as in q1a,

Implement

<ul>

 <li><strong>Sorted_List * map ( Sorted_List *, </strong><strong><em>fn ptr</em></strong><strong>)</strong> o map only applies to the values, not the sort keys</li>

</ul>

o however, make sure that the new list produced has the same key values  and links (both next and sort)

<ul>

 <li><strong>value_type reduce ( Sorted_List *, </strong><strong><em>reduce fn ptr</em></strong><strong>, value_type init, int order )</strong> o like map, reduce only applies to values, not keys</li>

</ul>

o however, reduce also takes an extra parameter, int order

<ul>

 <li>order is either INSERTED_ORDER or SORTED_ORDER and determines which set of links to follow while reducing: next or sort respectively</li>

 <li>note: while the order of the reduction does not matter when using add or mult              as the reducing function, it could with other reduction functions</li>

</ul>

<ul>

 <li><strong>value_type map_reduce (Sorted_List *list, </strong><strong><em>map fn ptr</em></strong><strong>, </strong><strong><em>reduce fn ptr</em></strong><strong>, value_type init, int order )</strong> o Conceptually, you are first applying map, and then reduce</li>

</ul>

o However, both map_fn and reduce_fn should be applied together, node-by-node

<ul>

 <li>e. do not create a full map list and then apply reduce to it</li>

 <li>instead apply the map function to list’s node, then store the result in the reduce accumulator</li>

</ul>

o This allows you to avoid creating and freeing the memory that would be used if an intermediate map list were to have been created and only then reduced

<ul>

 <li><strong>value_type * map_2_array ( Sorted_List *list1, List_Sort *list2, </strong><strong><em>fn ptr</em></strong><strong>, int order) </strong>o map_2_array takes two lists and applies a function, passed in as a function pointer, that takes two values (from the nodes at the same position in their respective lists) and returns a value of type value_type

  <ul>

   <li>The values are collected in an array with element type value_type in the same order as traversed along the links chosen (i.e. next if INSERTED_ORDER was chosen or sort if SORTED_ORDER was)</li>

   <li>the function then returns the above array</li>

  </ul></li>

</ul>

<em>note:            unlike map, order of traversal matters with map_2_array            as different nodes will be paired together depending on the order </em>

<ul>

 <li><strong>value_type map_2_reduce( Sorted_List *list1,</strong> <strong>List_Sort *list2,</strong> <strong><em>map fptr</em></strong><strong>,</strong> <strong><em>reduce fptr</em></strong><strong>,</strong> <strong>int</strong> <strong>order)</strong> o Similar to map_reduce,</li>

</ul>

o However, node by node, it should

<ul>

 <li>apply the map function to the value of list1’s node as its first argument and the value of list2’s node as its second argument</li>

 <li>then store the result in reduce’s accumulator</li>

</ul>




<strong>Below </strong><strong>list1 and list2 only depict the </strong><strong>value</strong><strong> and </strong><strong>next</strong><strong> fields</strong>

<strong>w</strong><strong>here </strong><strong>add</strong><strong> and </strong><strong>mult</strong><strong> are functions that take two </strong><strong>int</strong><strong> arguments as seen in the </strong><strong>reduce</strong><strong> example in the lecture notes</strong>




<h2>Figure 1:  Example of map_2array and map_2_reduce using INSERTED_ORDER</h2>
















<strong>list1 and list2 are the same as before,
 but now depict the </strong><strong>key</strong><strong> and </strong><strong>sort</strong><strong> fields where </strong><strong>key</strong><strong> was set equal to </strong><strong>value</strong>




<h2>Figure 2:  Example of map_2array and map_2_reduce using SORTED_ORDER</h2>




To test within, map, reduce, etc. <strong> </strong>

<em>Write a program called   </em>a4q1b.c

<ul>

 <li>Data types used

  <ul>

   <li>value_type datatype is equal to  int  o key_type  datatype is equal to  double o same as a4q1a_int.c, so compile files containing Sorted_List functions using -DINT</li>

  </ul></li>

 <li>The program reads in a text file that contains a series of commands, one per line, with the name of the text file entered as a command line argument o Base this code on the code you used in q1a to implement command entries from a file  o However, the code will need to be extended to allow for new commands that are detailed below</li>

 <li>Again, all commands are echoed to stdout, followed by a colon : in the same format as used with q1</li>

 <li>Include a void print_array(value_type *, int size) o this prints out values in the array produced by map_2_array

  <ul>

   <li>the values in the array should be printed one per line, with five spaces preceding the value</li>

  </ul></li>

 <li>Make sure you have declared an array that can hold up to 10 Sorted_List pointers o Do not confuse this with the array produced by map_2_array, this array holds Sorted_List pointers <strong>not</strong> value_type values.</li>

 <li>Remember to free all sorted lists and nodes (and arrays that may contain them) at the end of the program</li>

</ul>

<em>             </em>

<strong>To implement the new commands, write the following functions  </strong><em>use either map, reduce, map_reduce, map_2_array, or map_2_reduce when implementing  </em>

<em> </em>

<h2>• sum</h2>

o sums the values of a list and returns the sum o see lecture notes

<ul>

 <li><strong>diff </strong>o takes two sorted lists of the same size</li>

 <li>returns NULL if the sizes are different o produces an array whose values are the differences of the values in the sorted lists args o you should also take a third argument that can be set to SORTED_ORDER or INSERTED_ORDER in order to follow the appropriate links</li>

 <li><strong>square</strong> o takes a sorted list and produces a new sorted list whose value at a node  equals the original value (not key) squared</li>

</ul>

o the keys and links should be copied unchanged

<ul>

 <li><strong>sum_of_sq_diff </strong>o takes two sorted lists of the same size

  <ul>

   <li>returns NULL if the sizes are different o produces a value computed as follows:</li>

   <li>at each node position, take the difference between the values</li>

   <li>square the resulting difference</li>

   <li>sum across all nodes into a single result o you should also take a third argument that can be set to SORTED_ORDER or INSERTED_ORDER in order to follow the appropriate links</li>

  </ul></li>

</ul>







<strong>note:      these should be 1 or 2 line programs that take function pointers               to functions that are also only a few lines long </strong>

<strong>             </strong>

<strong>List of Commands  </strong>

All commands from q1a should be made available as well as the following

<strong><em>Silent Commands (modifies the list but does not print anything other than the command itself) </em></strong>

<ul>

 <li>a|<em>n</em> <em>key</em> <em>value</em>

  <ul>

   <li>append to the nth index of the array of sorted list pointers that you have set up for the program to use (see the 5<sup>th</sup> point on how to set up the program two pages back)</li>

   <li>same as the a command but appends the key/value pair into the array of sorted lists</li>

  </ul></li>

 <li>p|<em>n</em> <em>key</em> <em>value</em></li>

</ul>

o same as a|<em>n</em> except it pushes instead of appends the key/value pair into the array of sorted lists <em> </em>




<strong><em>Report Commands (prints information, but does not modify the list)</em></strong>

For all examples, the sorted list at index 3 holds the values &lt;1, 2, 3&gt; where the key equals the value    the sorted list at index 5 holds the values &lt;3, 1, 7&gt; where the key equals the value

<ul>

 <li>print_all|<em>n</em>

  <ul>

   <li>print the sorted list at index <em>n</em> in insertion order</li>

   <li>Using the input from the append examples in q1a that had been stored at index 2</li>

  </ul></li>

</ul>

For the command “print_all|2”, the output should be

print_all:  list = 2, Insertion Order

3.27  1427

0.94  984

7.21  346

<ul>

 <li>print_sort|<em>n</em></li>

</ul>

o print the sorted list at index <em>n</em> in key sort order

<ul>

 <li>sum|<em>n</em></li>

</ul>

o sums the values of the sorted list at index <em>n</em>  o For the command “sum|3”, the output should be sum:        list = 3, result = 6

<ul>

 <li>square|<em>n</em> o For the command “square|3”, the output should be square: list = 3</li>

</ul>

1.0  1

2.0  4

3.0  9

o remember to free any new list produced, after it has been printing

<ul>

 <li>diff|<em>n</em>:<em>m order</em>  o For the command “diff|5:3  INSERTED_ORDER”, the output should be diff:       list1 = 5, list2 = 3, Insertion Order</li>

</ul>

2

-1

4 o remember to free any new list produced, after it has been printing

<ul>

 <li>sum_sq_d|<em>n</em>:<em>m order</em> o For the command “sum_sq_d |5:3  INSERTED_ORDER”, the output should be sum_sq_d:   list = 5, list2 = 3, Insertion Order, result = 21</li>

</ul>

The assignment continues with Question 2: Recursion




<h1>Question 2: Recursion</h1>




<h2>2a.       Recursive functions</h2>

<ul>

 <li>Implement the following functions using recursion (<em>see the next page for examples</em>) o Count up from 0 to n o Count down from 2n to 0 by 2 o nth, nth_sorted</li>

 <li>this applies to Sorted Lists from Q1a o remove_nth, remove_nth_sorted</li>

 <li>this applies to Sorted Lists from Q1a</li>

</ul>

<em>note:  no marks will be awarded if implemented iteratively,               even if the answer produced is correct when run  </em>




<h2>2b.        Greatest Common Divisor (GCD)</h2>

<ul>

 <li>Read up on the Euclidean Algorithm for solving GCD in Wikipedia o First Section: <u>https://en.wikipedia.org/wiki/Euclidean_algorithm</u> o Procedure: <u>https://en.wikipedia.org/wiki/Euclidean_algorithm#Procedure</u>  o Example: <u>https://en.wikipedia.org/wiki/Euclidean_algorithm#Worked_example</u>  o Using mod: <u>https://en.wikipedia.org/wiki/Euclidean_algorithm#Euclidean_division</u>  o Implementations: <u>https://en.wikipedia.org/wiki/Euclidean_algorithm#Implementations</u></li>

 <li>Examine the final implementation, which is recursive, and implement it in C o it should have the signature long gcd(long, long)</li>

 <li>This implementation (as yours should be) is naturally “tail recursive” o <strong>explain why it is tail recursive in the readme </strong></li>

</ul>

o <strong>make sure your make file uses the appropriate gcc flag</strong> to run tail recursive code efficiently




<h2>To test question 2</h2>

<em>Write a program called   </em>a4q2.c

<ul>

 <li>The program must read in a text file that contains a series of commands, one per line, with the name of the text file entered as a command line argument o Base this code on the code you used in q1a to implement command entries from a file  o However, the code will need to be extended to allow for new commands that are detailed below</li>

 <li>Some of the questions in 2a use the Sorted_List data type with key_type as double and value_type as int, the same as a4q1a_int.c.</li>

</ul>

o So when compiling files containing Sorted_List functions in your make file, use –DINT

<ul>

 <li>All new commands for entry from the input file are listed on the next page</li>

</ul>




<h2>The assignment concludes with Question 3: Fraction ADT  to be released early next week</h2>

<strong>             </strong>

<strong>List of Commands from the Input File  </strong>

All commands from q1a should be made available as well as the following

<ul>

 <li>count_up <em>n</em></li>

</ul>

o Prints the integers from 0 to <em>n</em> on a single line, comma separated, with 5 spaces before o Using the following commands       count_up 4 the output should be

count_up from 0 to 4

0, 1, 2, 3, 4

<ul>

 <li>count_down <em>n</em></li>

</ul>

o Same as count_up, but printing the integers down from 2<em>n</em> to 0 on by 2  o Using the following commands       count_down 4 the output should be

count_down from 8 to 0 by 2

8, 6, 4, 2, 0

<ul>

 <li>nth <em>n</em> <em>order</em> o Displays the nth element in the list according to the order specified (inserted or key sort) on its own line as <em>key  value</em>

  <ul>

   <li>Indented 5 spaces with 2 spaces between the key and the value</li>

   <li>Firsts prints the command – see below for an example o Using the input from the append examples in q1a and the following commands print_all  nth 1 INSERTED_ORDER  nth 1 SORTED_ORDER  nth 5 INSERTED_ORDER the output should be</li>

  </ul></li>

</ul>

print_all:  Insertion Order

3.27  1427

0.94  984

7.21  346

nth:        n = 1, Insertion Order

0.94  984

nth:        n = 1, Key Sort Order

3.27  1427

nth:        n = 5, FAILED, n &gt;= size where size = 3

<ul>

 <li>remove_nth <em>n order</em> o removes the nth element in the list according to the order specified (inserted or key sort) and displays the removed element on its own line as <em>key  value</em></li>

</ul>

o Again using the input from the append examples in q1a For the commands

remove_nth 2 INSERTED_ORDER  print_all

remove_nth 1 SORTED_ORDER  print_all

the output should be

remove_nth: n = 2, Insertion Order

7.21  346

print_all:  Insertion Order

3.27  1427

0.94  984

remove_nth: n = 1, Key Sort Order

3.27  1427

print_all:  Insertion Order

0.94  984




<h1>Question 3: Interacting Abstract Data Types –</h1>




<h2>New ADT – Fraction</h2>

You may<strong> not</strong> use functions from any C library that implements fractions

typedef struct {     long num;     long denom;     /* you may also use “unsigned long denom”, either approach is fine */

} Fraction;

<ul>

 <li>Implement int set_fraction(Fraction * fract, int num, int denom)

  <ul>

   <li>Sets the numerator and denominator in the Fraction structure o Only the numerator can be negative

    <ul>

     <li>If the denom parameter is negative, negate the num parameter and store denom in the struct as a positive value</li>

    </ul></li>

   <li>The denom parameter cannot be 0

    <ul>

     <li>If it is zero do not set the num and denom in fract and return FALSE (where FALSE is a #define set to 0)</li>

    </ul></li>

   <li>If the num and denom can be successfully set, return TRUE</li>

  </ul></li>

</ul>

(where TRUE is a #define set to 1)

<ul>

 <li>Implement print_fract(Fraction * fract, int mode) o When mode is SIMPLE

  <ul>

   <li>Print out num/denom</li>

   <li>If fract has num = 4 and a denom = 3 it should print “4/3” to stdout o When mode is MIXED</li>

   <li>If fract has num = 3 and a denom = 4, print “3/4” to stdout</li>

   <li>If fract has num = 4 and a denom = 3, print “1 1/3” to stdout</li>

   <li>If fract has num = 4 and a denom = 1, print “4” to stdout o SIMPLE and MIXED are two integers of your choice, using #define in a .h</li>

  </ul></li>

 <li>Implement void simplify(Fraction * fract)

  <ul>

   <li>This is computed by finding the GCD of the numerator and the denominator and dividing it out from each respectively i.e. for a / b</li>

  </ul></li>

 <li>find g = gcd(a, b)</li>

 <li>the simplified form of a / b is</li>

</ul>

(a/g) / (b/g)

<ul>

 <li>e.g. 6/18</li>

 <li>gcd(9, 12) == 3 (9/3) / (12/3) == 3 / 4</li>

</ul>

<em>note: when you wrote GCD for Q2, qcd(a,b) should equal gcd(b,a) </em>




<ul>

 <li>Implement int add_fract(Fraction * result, Fraction * x, Fraction * y)</li>

</ul>

o To compute <em>a</em>/<em>b</em> + <em>c</em>/<em>d</em>, i.e. to add two fractions, use the following formula

(<em>a</em> <em>d</em> + <em>b</em> <em>c</em>)/<em>b</em> <em>d</em> , simplified o Check to make sure that the result doesn’t overflow/underflow

<ul>

 <li>e the addition produces a result greater than a long can represent</li>

 <li>when the result is positive it is called an overflow</li>

 <li>when negative it is called an underflow o to check for an overflow/underflow, understand and use the solution posted in the most popular reply from the following stackoverflow page</li>

 <li><u>https://stackoverflow.com/questions/199333/how-do-i-detect-unsigned-integer-multiply-overflow</u> o If the addition overflows/underflows, return FALSE and do not update fract o Otherwise return TRUE</li>

</ul>

<strong> </strong>

<h2>Extend Map/Reduce/etc. with Filter</h2>

<ul>

 <li>Implement Sorted_List * filter (Sorted_List * list, filter_fn pointer)</li>

 <li>the function creates a <strong>new</strong> sorted list based on the filtered values (added node by node), remember the nodes have to be copied</li>

 <li>the function filters based on the value, not the key o for full marks, implement filter() using recursion</li>

 <li>store filter() in the same .c file where the other map/reduce/ etc. functions are stored</li>

 <li>you do not need to submit two different .c files, just one will do • filter will just not be exercised when the Q1b is tested</li>

</ul>




<h2>To test question 3</h2>

<em>Write a program called   </em>a4q3.c

<ul>

 <li>The program must read in a text file that contains a series of commands, one per line, with the name of the text file entered as a command line argument o Base this code on the code you used in q1a to implement command entries from a file  o However, the code will need to be modified as detailed below</li>

 <li>You will need to store fractions in a sorted list using the Sorted_List data type o value_type should be of type Fraction</li>

</ul>

o key_type should be a double and hold the decimal equivalent of the value stored in the Node

<ul>

 <li>e.g. if value stores the fraction 11/4, then key == 2.75</li>

 <li>You will have to have your make file recompile all files that mention or use value_type and key_type variables or Sort_List structs when compiling the program o You will need to add #ifdef FRACT to compile using the Fraction typedef definition  of value_type</li>

</ul>

o E.g. if you stored all your Sort_List ADT functions in a single file called sort_list.c  Then for a4q4.c you could have in your make file a command like




gcc  -Wall -ansi -DFRACT -c sort_list.c

<ul>

 <li>All commands for entry from the input file are listed on the next couple of pages</li>

</ul>




<strong>             </strong>

<strong>List of Commands from the Input File </strong>

You only need a single Sorted List, like in q1a, and q2, not the array of sorted lists as in q1b

<strong><em>Silent Commands (modifies the list but does not print anything other than the command itself) </em></strong>

<ul>

 <li>a <em>n</em>/<em>d</em></li>

</ul>

o appends to a sorted list

<ul>

 <li>with <em>n</em> stored in the numerator field of the Fraction held in node-&gt;value<em>, </em>and <em>d</em> stored in the denominator field of the Fraction</li>

 <li>the decimal value equivalent of the fraction should be stored in the key field</li>

</ul>

<em>note:  when echoing the command, the fraction is output without simplification          and the key is displayed with 3 decimal places </em>o example

<ul>

 <li><em>commands, as stored in the input file</em>               a   5/4     a   3         a   4/6</li>

 <li><em>output</em>(11 – 1 spaces after the colon)</li>

</ul>

a:          1.250  5/4                a:          3.000  3                 a:          0.667  4/6

<ul>

 <li>p <em>n</em>/<em>d</em></li>

</ul>

o same as a except it pushes instead of appends the key-value pair onto the sorted list

<strong><em>Report Commands (prints information, but does not modify the list) </em></strong>

<ul>

 <li>print_all <em>print_mode</em></li>

</ul>

o print the sorted list at index <em>n</em> in insertion order  o Using the input from the append examples above

For the command “print_all SIMPLE”, the output should be

print_all:  Simple Fractions, Insertion Order

1.250  5/4

3.000  3/1

0.667  2/3

<ul>

 <li>print_sort <em>print_mode</em></li>

</ul>

o print the sorted list at index <em>n</em> in key sort order o Using the input from the append examples above

For the command “print_sort MIXED”, the output should be  print_all:  Mixed Fraction, Sorted Order

0.667  2/3

1.250  1 1/4

3.000  3




<ul>

 <li>sum <em>print_mode</em> o sums the values of the sorted list into a simplified fraction, which is printed (in insertion order) o Using the input from the append examples above For two commands   sum  SIMPLE    sum  MIXED</li>

</ul>

the output should be

sum:        result = 4 11/12   sum:        result = 59/12

o If the sum enters an overflow situation, the output should be  sum:        result = OVERFLOW

<ul>

 <li>This could happen in either the numerator or denominator at any point in the calculation</li>

 <li>If the numerator would be negative, instead of OVERFLOW, it should print UNDERFLOW</li>

</ul>

<ul>

 <li>fract <em>print_mode</em> o uses the filter function to only keep fractions and ignore whole numbers when producing the new sorted list; then print the filtered list</li>

</ul>

o remember to free the new list produced by filter after printing

(hint: you had to do that for various commands in q1b as well) o Using the input from the append examples above

For the command “fract MIXED”, the output should be  fract:      Mixed Fractions, Insertion Order

1.250  1 1/4

0.667  2/3

<ul>

 <li>whole_num <em>print_mode</em> o similar to fract except it uses the filter function to filter out all fractions leaving only the whole numbers in the new list</li>

</ul>

o Using the input from the append examples above

For the command “whole_num MIXED”, the output should be

whole_num:  Mixed Fractions, Insertion Order       3.000  3

<ul>

 <li>rem_mixed <em>print_mode</em> o similar to fract except it uses the filter function to keep only the whole numbers and simple fractions (removes the mixed numbers)</li>

 <li>i.e. leaving out the numbers that, when printed as MIXED, have both a whole number and fraction parts, such as    7 2/3</li>

</ul>

o Using the input from the append examples above

For the command “rem_mixed MIXED”, the output should be

rem_mixed:  Mixed Fractions, Insertion Order

3.000  3

0.667  2/3


