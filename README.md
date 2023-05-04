Download Link: https://assignmentchef.com/product/solved-cse-231-programming-project-08
<br>
<h1>Assignment Overview</h1>




<ul>

 <li>Dictionaries and Lists</li>

 <li>File manipulation</li>

</ul>




<h1>Assignment Background</h1>




Video games have become an outlet for artists to express their creative ideas and imaginations and a great source of entertainment for people who seek a fun and accessible ways to immerse in unique worlds while also share and interact with others. This project will print video game sales data for various platforms across the years. From the old school consoles like Atari 2600 and Sega Genesis to more modern ones like the Xbox One and PlayStation 4.




<h1>Project Specifications</h1>

You must implement the following functions:




<strong>open_file () </strong>à<strong> file pointer:</strong>

<ol>

 <li>This function repeatedly prompts the user for a filename until the file is opened successfully. An error message should be shown if the file cannot be opened. It returns a file pointer. Use try-except and FileNotFoundError to determine if the file can be opened. Use the ‘utf-8’ encoding to open the file.</li>

</ol>

fp = open(filename, encoding =’utf-8’)




<ol>

 <li>Parameters: none</li>

 <li>Returns : file pointer</li>

</ol>




<strong> </strong>

<strong>read_file (fp) </strong>à<strong> D1,D2,D3:</strong>

<ol>

 <li>This function read a file pointer and returns 3 dictionaries:

  <ul>

   <li>Parameters: file pointer (fp)</li>

   <li>Returns : 3 dictionaries of list of tuples</li>

   <li>The function displays nothing</li>

  </ul></li>

</ol>




<ol>

 <li>You must use the reader because some fields have commas in them.</li>

</ol>




<ol>

 <li>Each row of the file contains the name of a video game, the platform which it was released, the release year, the genre (i.e. shooter, puzzle, rpg, fighter, etc.), the publishing company, and regional sales across north America, Europe, Japan, and other regions. For this project, we are only interested in the following columns:</li>

</ol>




name = line[0] platform = line[1] year = int(line[2]) genre = line[3] publisher = line[4] na_sales = float(line[5]) europe_sales = float(line[6]) japan_sales = float(line[7]) other_sales = float(line[8])

<strong> </strong>

<ol>

 <li><strong>All strings should be converted to lower case and stripped of the trailing/forward white spaces. </strong></li>

</ol>

<strong> </strong>

<ol>

 <li><strong>Multiply each regional sales column by 1,000,000. </strong>The program must compute the total global sales by adding all the regional sales (na_sales, europe_sales, japan_sales, other_sales).</li>

</ol>




<ol>

 <li>This function returns 3 separate dictionaries. The first dictionary, with ‘name’ as key, will contain the data used to display the global sales per year or platform. The second dictionary, with ‘genre’ as key, contains the data used to display the regional sales per genre. The third dictionary, with ‘publisher’ as key, contains the data used to display the global sales by publisher. All of 3 dictionaries have a list of tuples as values:</li>

</ol>







D1 = { name:[(name, platform, year, genre, publisher, global_sales), …], …}

D2 = { genre: [(genre, year, na_sales, eur_sales, jpn_sales, other_sales, global_sales), …], …}

D3 = {publisher: [(publisher, name, year, na_sales, eur_sales, jpn_sales, other_sales, global_sales), …], …}




You should ignore all the values that are not valid:

<ul>

 <li>‘year’ should be integer (int)</li>

 <li>All regional sales should be floats (floats).</li>

</ul>




<ol>

 <li>Once the file is read and all the data is stored in the 3 dictionaries, you need to sort each dictionary alphabetically in ascending order by their keys. The values for the 3 dictionaries should also be sorted by the last element of the tuples in reverse order</li>

</ol>

(global_sales).

<strong>Hint: Dictionaries are insertion sorted meaning the order of insertion into the dictionary is preserved. You should first get all the keys of a dictionary and sort them. Then iterate through the sorted list of keys and insert their corresponding values into a new dictionary. You should sort the values before inserting them. </strong>




<strong>get_data_by_column(D1, indicator, c_value) </strong>à<strong> List of tuples:</strong>

<ol>

 <li>This function iterates through the dictionary D1 and return a subset of the data as indicated in (b) below.

  <ul>

   <li>Parameters: Dictionary (D1), indicator (str), c_value (str or int) – Returns : List of tuples</li>

   <li>The function displays nothing</li>

  </ul></li>

</ol>

<strong> </strong>

<ol>

 <li>The indicator parameter is a string with two values: ‘year’ or ‘platform’. If indicator equals to ‘year’, append all tuples whose value at the year column is equal to c_value into the new list. Sort the new list by global sales (global_sales) in descending order and then by the platform alphabetically.</li>

</ol>

If indicator equals to ‘platform’, append all tuples whose value at the platform column is equal to c_value into the new list. Sort the new list by global sales (global_sales) in descending order and then by the year in ascending order.




<ol>

 <li>If the c_value does not exist in the data, the function should return an empty list.</li>

</ol>

<strong>get_publisher_data(D3, publisher) </strong>à<strong> List of tuples:</strong>




<ol>

 <li>This function iterates through the dictionary D3 (which contains the publisher data with publisher as the D3 key). It will return a list of all tuples where the publisher key equals the publisher <strong> </strong>

  <ul>

   <li>Parameters: Dictionary (D3), publisher (str)</li>

   <li>Returns : List of tuples</li>

   <li>The function displays nothing</li>

  </ul></li>

</ol>

<strong> </strong>

<ol>

 <li>The list should be sorted by name alphabetically and by global sales (global_sales) in descending order. Since the sorted function and the sort method are stable sorts, you can first sort the names of the games alphabetically, and then sort them by global sales (with reverse=True). (You do the two sorts in that order because you do the primary key last, global_sales is the primary key in this case.) By default, sorting is done on the first item in a list or tuple. To sort on other items use itemgetter from the operator</li>

</ol>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong>display_global_sales_data(L1, indicator)</strong>




<ol>

 <li>This function prints a table of all the global game sales stored in L1 by either all platforms in a single year or all years for a single platform. This function does not return anything.

  <ul>

   <li>Parameters: List of tuples(L1), indicator (str)</li>

   <li>Returns : nothing</li>

  </ul></li>

</ol>

<strong> </strong>

<ol>

 <li>The list of tuples (L1) is the list returned from the get_data_by_column()</li>

 <li>The indicator parameter is a string with two values: ‘year’ or ‘platform’. If indicator equals to ‘year’, display the video game sales in one year (‘Name’, ‘Platform’, ‘Genre’, ‘Publisher’, ‘Global Sales’).</li>

</ol>

If indicator equals to ‘platform’, display video game sales for that platform (‘Name’,

‘Year’, ‘Genre’, ‘Publisher’, ‘Global Sales’).




For all the cases, the header row uses the following format:

“{:30s}{:10s}{:20s}{:30s}{:12s}”

The following rows uses the following string formatting:

“{:30s}{:10s}{:20s}{:30s}{:&lt;12,.02f}”

Truncate (using slicing) the name and publisher to 25 characters, and the genre to 15 characters.




<ol>

 <li>The sum of total global sales should be calculated and displayed. The following string formatting should be used to display the total:</li>

</ol>

“
{:90s}{:&lt;12,.02f}”

<strong> </strong><strong>get_genre_data(D2, year) </strong>à<strong> List of tuples: </strong>




<ol>

 <li>This function iterates through the dictionary D2 (which contains the list of regional sales by genre) and return a list of the total regional sales per genre whose value at the year column is equal to ‘year’.

  <ul>

   <li>Parameters: Dictionary (D2), year (int)</li>

   <li>Returns : List of tuples</li>

  </ul></li>

</ol>




<ol>

 <li>The list of tuples should include the following information:</li>

</ol>

[(genre, count, total_na_sales, total_eur_sales, total_jpn_sales, total_other_sales, total_global_sales), …],

Where:

genre: genre name

count: number of games per genre (or number of occurrences of genre in that year) total_na_sales: total sales in North America

total_eur_sales: total sales in Europe total_jpn_sales: total sales in Japan total_other_sales: total sales in other regions total_global_sales: total sales in all regions




<ol>

 <li>Before returning the list, sort the extracted data by genre name alphabetically and then sort this data by global sales in descending order.</li>

 <li>If the year does not exists in the data, the function should return an empty list.</li>

 <li>Hint: check the count (index 1 of your tuple) before appending a tuple onto your genre list. If the count is zero, do not append it.</li>

</ol>

<strong>display_genre_data(genre_list):</strong>




<ol>

 <li>a) This function prints a table of all the total regional sales for each genre stored in genre_list. This function does not return anything.</li>

 <li>Parameters: genre_list(list)</li>

 <li>Returns : nothing</li>

</ol>

<strong> </strong>

<ol>

 <li>The list of tuples (genre_list) is the list returned from the get_genre_data() function (which was called in main under Option 3).</li>

 <li>The header row (provided in the skeleton code) uses the following format:</li>

</ol>

“{:15s}{:15s}{:15s}{:15s}{:15s}{:15s}”

The following rows uses the following string formatting:

“{:15s}{:&lt;15,.02f}{:&lt;15,.02f}{:&lt;15,.02f}{:&lt;15,.02f}{:&lt;15,.02f}”







<ol>

 <li>The sum of total global sales should calculated and be displayed. The following string formatting should be used to display the total:</li>

</ol>

“
{:75s}{:&lt;15,.02f}”

<strong>display_publisher_data(pub_list):</strong>




<ol>

 <li>a) This function prints a table of all the total regional sales for each genre stored in pub_list. This function does not return anything.</li>

 <li>Parameters: pub_list(list)</li>

 <li>Returns : nothing</li>

</ol>

<strong> </strong>

<ol>

 <li>The list of tuples (pub_list) is the list returned from the get_ publisher_data()</li>

 <li>The header row uses the following format:</li>

</ol>

“{:30s}{:15s}{:15s}{:15s}{:15s}{:15s}”

The following rows uses the following string formatting:

“{:30s}{:&lt;15,.02f}{:&lt;15,.02f}{:&lt;15,.02f}{:&lt;15,.02f}{:&lt;15,.02f}”

Note: “Title” in the header refers to name in the tuple in pub_list, i.e. index 1, and it must be truncated to 25 characters (Hint: slice).







<ol>

 <li>The sum of total global sales should be calculated and displayed. The following string formatting should be used to display the total:</li>

</ol>

“
{:90s}{:&lt;15,.02f}”

<strong> </strong><strong>get_totals(L, indicator) </strong>à<strong> List, List: </strong>




<ol start="2">

 <li>This function receives a list L of tuples with global sales that was generated by the <strong>get_data_by_column</strong>   As in that function, there are two values for indicator: “year” a list of global sales per platform for a single year (from Menu option 1 in main) or “platform” a list of global sales per year for a single platform (from Menu option 2 in main). The function returns two lists: L1, the one with the strings of each platform name (if indicator == “year” ) or the integers of each year (if indicator == “platform” ), and the other, L2, is the corresponding global sales. (These two lists will be used for plotting in option 1 and 2. )

  <ul>

   <li>Parameters: L (List), indicator (str)</li>

   <li>Returns : List, List – The function displays nothing</li>

  </ul></li>

</ol>

<strong> </strong>

<ol>

 <li>You need to collect global sales for each platform (or year). The easiest way to do that is with a dictionary with the key is platform (or year) and the value is the sales for that platform (or year).  You then build a list, L1, of keys (platforms or years) and a list, L2, of their corresponding values (sales).  The first list, L1,  should be sorted by platform or year (depending on the value of indicator ) in ascending order. L2 needs to have the corresponding values in the same order as L1. (Hint: create and sort L1 and then use the items in L1 and your dictionary of sales to build L2 such that the key:value relationship is maintained in L1:L2.) Return the lists as L1 first and then L2.</li>

</ol>

<strong> </strong><strong>prepare_pie(L) </strong>à<strong> List, List: </strong>




<ol>

 <li>This function receives a list of global sales per genre for a particular year (that is, the list L comes from a call to get_genre_data for a particular year, the call being done in option 3 of main). It returns two lists: L1, one with the strings of each genre name, and the other, L2, is total global sales in that year. These two lists will be used for plotting in option 3 so each genre name in list L1 has its corresponding total global sales in L2 at the same index.

  <ul>

   <li>Parameters: L (List)</li>

   <li>Returns : List, List – The function displays nothing</li>

  </ul></li>

</ol>

<strong> </strong>

<ol start="2">

 <li>The list L2 should be sorted by total_global_sales in descending order and L1 should be sorted so the genre name corresponds with the total global sales in L2. Hint:</li>

</ol>

create a list of tuples that you sort first by name and then by sales.  Then create the separate lists L1 and L2. <strong>main()</strong> :




<ol>

 <li>a) This function is the starting point of the program. The program starts by opening the file with the video game sales and reading the data into three dictionaries. The program will repeatedly prompt the user to select an option from the following menu:</li>

</ol>




<ol>

 <li><strong>Option 1:</strong> Display the global sales for all video game titles across multiple platforms in a single year. Prompt for a year (validation is required!, year needs to be an int), get the data by calling the get_data_by_column function, and then display the selected year’s data if the year exists in the data. Prompt the user whether they want to plot the data. If the answer is “y”, use plot_global_sales() to plot the histogram of the total global sales per publisher.</li>

</ol>

<strong> </strong>

<ol>

 <li><strong>Option 2:</strong> Display the global sales for all video game titles across multiple years in a single platform. Prompt for a platform (validation is required!, cannot be a number) ), get the data by calling the</li>

</ol>

get_data_by_column function, and then display the selected platform data if the platform exists in the data. Prompt the user whether they want to plot the data. If the answer is “y”, get lists to plot by calling the get_totals function, and then use plot_global_sales() to plot the histogram of the total global sales per year.




<ul>

 <li><strong>Option 3:</strong> Display the regional sales for all video game genres. Prompt for a year (validation is required!, year needs to be an int), call get_genre_data, and then display the selected year data if the year exists using display_genre_data. Prompt the user whether they want to plot the data. If the answer is “y”, call prepare_pie to get the lists to plot, and then use plot_genre_pie() to plot a pie chart of the total global sales per genre.</li>

</ul>

<strong> </strong>

<ol>

 <li><strong>Option 4:</strong> Display the regional sales for all the video games by publisher. Prompt the user for a keyword in the publisher. Search for all publishers who have that keyword as a substring, then display the results. <strong>If there are multiple publisher names with the same string, enumerate all possible names</strong>. The publisher names should appears alphabetically because they were read into the dictionary that way; if not, sort them. Use the following string formatting:</li>

</ol>

“{:&lt;4d}{}”.format(index,publisher)




Prompt the user for a publisher index from the displayed list (validation is required!; check that the publisher exists in D3) and display the selected publisher data.

<strong> </strong>

<ol>

 <li><strong>Option 5:</strong> Stop the program.</li>

</ol>




If the user does not enter any of these options, the program needs to display an error message and prompt again until a valid option is selected.




<ol start="2">

 <li>Hints and Notes</li>

 <li>Need to print a header line? Using multiple string inside a format method, use the “*” operator to unpack the list. Unpacking is used with iterable items (e.g. lists, strings, and tuples) to take each individual value of the iterable and assign it to various argument positions. In other words, each element from the iterable becomes an individual value. For example:</li>

</ol>




lst = [“I”, “Love”, “Python!”] print(“{} {} {}”.format(*lst)) # This prints: I love Python!




<ol>

 <li>Provided functions:

  <ol>

   <li><strong>plot_global_sales(x,y): </strong></li>

  </ol></li>

</ol>

This function creates bar plots when the user wants to process the global sales data by year or platform. It receives a list of publishers or years and a list of global sales. The bar plots the global sales for each publisher or year. It returns nothing.

<ul>

 <li>Parameters: x (List), y (List)</li>

 <li>Returns : nothing</li>

 <li>The function displays nothing</li>

</ul>

<strong> </strong>

<ol>

 <li><strong>plot_genre_pie(genre, values): </strong>This function creates a pie plot when the user wants to process the global sales data by genre in a particular year. It receives a list of genres and a list of global sales for a year. It returns nothing.

  <ul>

   <li>Parameters: x (List), y (List)</li>

   <li>Returns : nothing</li>

   <li>The function displays nothing</li>

  </ul></li>

</ol>




<h1>Deliverables</h1>




The deliverable for this assignment is the following file:

proj08.py – the source code for your Python program

Be sure to use the specified file name and to submit it for grading via Mimir before the project deadline.

<h1>(See Mimir for function tests details)</h1>

<strong>             </strong>

<strong>Test Case 1: </strong>




Enter filename: video_game_sale_2016.csv File not found! Please try again!




Enter filename: video_game_sales_2016.csv




Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 8

Invalid option. Please Try Again!




Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 1




Enter year: 1900

The selected year was not found in the data.




Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 2




Enter platform: sega

The selected platform was not found in the data.




Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 3




Enter year: xyz

Invalid year




Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 4




Enter keyword for publisher: gotta catch ’em all!

No publisher name containing “gotta catch ’em all!” was found!




Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 5




Thanks for using the program!

I’ll leave you with this: “All your base are belong to us!”




<strong>             </strong>

<strong>Test Case 2: </strong>




Enter filename: video_game_sales_small.csv Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 4

Enter keyword for publisher: act There are 32 publisher(s) with the requested keyword!

<ul>

 <li>activision</li>

 <li>activision value</li>

 <li>avalon interactive</li>

 <li>bigben interactive</li>

 <li>bmg interactive entertainment</li>

 <li>disney interactive studios</li>

 <li>dreamworks interactive</li>

 <li>eidos interactive</li>

 <li>empire interactive</li>

 <li>focus home interactive</li>

 <li>fox interactive 11 game factory</li>

 <li>gremlin interactive ltd</li>

 <li>gt interactive</li>

 <li>hasbro interactive</li>

 <li>hip interactive 16 idea factory</li>

 <li>idea factory international</li>

 <li>marvelous interactive</li>

 <li>mattel interactive</li>

 <li>mentor interactive</li>

 <li>midas interactive entertainment</li>

 <li>simon &amp; schuster interactive</li>

 <li>take-two interactive</li>

 <li>tdk mediactive</li>

 <li>time warner interactive</li>

 <li>tripwire interactive</li>

 <li>universal interactive</li>

 <li>victor interactive</li>

 <li>virgin interactive</li>

 <li>warner bros. interactive entertainment</li>

 <li>xicat interactive</li>

</ul>

Select the index for the publisher to use: 5

Video Games Sales for disney interactive studios

Title                         North America  Europe         Japan          Other          Global          epic mickey                   2,040,000.00   630,000.00     120,000.00     220,000.00     3,010,000.00    who wants to be a million     1,940,000.00   0.00           0.00           0.00           1,940,000.00    toy story mania!              1,040,000.00   660,000.00     0.00           180,000.00     1,880,000.00    disney infinity               970,000.00     340,000.00     0.00           130,000.00     1,440,000.00    disney infinity 3.0           240,000.00     370,000.00     0.00           120,000.00     730,000.00      disney infinity 2.0: marv     270,000.00     250,000.00     0.00           100,000.00     620,000.00      epic mickey: power of ill     360,000.00     40,000.00      40,000.00      40,000.00      480,000.00      pirates of the caribbean:     300,000.00     10,000.00      10,000.00      30,000.00      350,000.00      pirates of the caribbean:     230,000.00     10,000.00      0.00           20,000.00      260,000.00      that’s so raven: psychic      230,000.00     0.00           0.00           20,000.00      250,000.00      the suite life of zack &amp;      230,000.00     0.00           0.00           20,000.00      250,000.00      disney stitch jam             70,000.00      0.00           160,000.00     10,000.00      240,000.00      disney’s a christmas caro     210,000.00     10,000.00      0.00           20,000.00      240,000.00      the chronicles of narnia:     150,000.00     40,000.00      0.00           10,000.00      200,000.00      disney’s home on the rang     120,000.00     40,000.00      0.00           0.00           160,000.00      fantasia: music evolved       110,000.00     30,000.00      0.00           10,000.00      150,000.00      tim burton’s the nightmar     100,000.00     40,000.00      0.00           0.00           140,000.00      walt disney pictures pres     90,000.00      30,000.00      0.00           0.00           120,000.00      disney planes fire &amp; resc     10,000.00      80,000.00      0.00           10,000.00      100,000.00      disney’s planes               40,000.00      30,000.00      0.00           10,000.00      80,000.00       tron 2.0: killer app          40,000.00      20,000.00      0.00           0.00           60,000.00




Total Sales

12,700,000.00

Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 5




Thanks for using the program!

I’ll leave you with this: “All your base are belong to us!”<strong> Test Case 3: </strong>




Enter filename: video_game_sales_2016.csv




Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 1




Enter year: 1999




Video Game Sales in 1999

Name                          Platform  Genre               Publisher                     Global Sales nfl 2k                        dc        sports              sega                          1,190,000.00 shenmue                       dc        adventure           sega                          1,180,000.00 seaman                        dc        simulation          sega                          520,000.00   sega rally championship 2     dc        racing              sega                          410,000.00   j-league pro soccer club      dc        sports              sega                          360,000.00   soulcalibur                   dc        fighting            namco bandai games            340,000.00   virtua striker 2              dc        sports              sega                          320,000.00   pro yakyuu team o tsukuro     dc        sports              sega                          230,000.00   tokyo xtreme racer            dc        racing              genki                         170,000.00   the king of fighters: dre     dc        fighting            snk                           100,000.00   blue stinger                  dc        adventure           activision                    100,000.00   marvel vs. capcom: clash      dc        fighting            capcom                        100,000.00




<h1>(To many titles to show in this document! See Mimir test for full view or “output3.txt”)</h1>




samurai shodown: warrios      ps        fighting            snk                           10,000.00    derby stallion                sat       sports              ascii entertainment           90,000.00    fire emblem: thracia 776      snes      strategy            nintendo                      260,000.00   digimon adventure: anode      ws        role-playing        namco bandai games            280,000.00   chocobo no fushigi dungeo     ws        role-playing        namco bandai games            180,000.00

Total Sales                                                                               251,110,000.00

Do you want to plot (y/n)? n




Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 2




Enter platform: gen




Video Game Sales for gen

Name                          Year      Genre               Publisher                     Global Sales streets of rage               1990      action              sega                          2,600,000.00 sonic the hedgehog            1991      platform            sega                          4,330,000.00 sonic the hedgehog 2          1992      platform            sega                          6,020,000.00 mortal kombat                 1992      fighting            arena entertainment           2,670,000.00 nba jam                       1992      sports              arena entertainment           2,050,000.00 street fighter ii’: speci     1992      fighting            sega                          1,650,000.00 gunstar heroes                1992      shooter             sega                          130,000.00   ecco the dolphin              1992      adventure           sega                          120,000.00   shining force ii              1993      strategy            sega                          190,000.00   super street fighter ii       1993      fighting            capcom                        150,000.00   ecco: the tides of time       1993      adventure           sega                          70,000.00    street fighter ii’: speci     1993      action              capcom                        70,000.00    streets of rage 3             1993      action              sega                          70,000.00    dynamite headdy               1993      platform            sega                          50,000.00    beyond oasis                  1993      role-playing        sega                          50,000.00    sonic &amp; knuckles              1994      platform            sega                          1,820,000.00 sonic the hedgehog 3          1994      platform            sega                          1,760,000.00 disney’s the lion king        1994      platform            virgin interactive            1,420,000.00 mortal kombat 3               1994      fighting            acclaim entertainment         1,340,000.00 nba jam tournament editio     1994      sports              acclaim entertainment         1,120,000.00 virtua racing                 1994      racing              sega                          260,000.00   lunar 2: eternal blue(sal     1994      role-playing        game arts                     140,000.00   yuu yuu hakusho: makyo to     1994      fighting            sega                          80,000.00    dragon slayer: the legend     1994      role-playing        sega                          80,000.00    j-league pro striker 2        1994      sports              sega                          40,000.00    castlevania bloodlines        1994      platform            konami digital entertainm     40,000.00    puzzle &amp; action: tant-r       1994      misc                sega                          30,000.00

Total Sales                                                                               28,350,000.00




Do you want to plot (y/n)? n




Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 3




Enter year: 2016




Regional Video Games Sales per Genre

Genre          North America  Europe         Japan          Other          Global          shooter        16,240,000.00  15,900,000.00  1,060,000.00   5,020,000.00   38,220,000.00   action         9,290,000.00   10,680,000.00  7,070,000.00   3,070,000.00   30,110,000.00   sports         7,540,000.00   12,010,000.00  920,000.00     3,020,000.00   23,490,000.00   role-playing   5,890,000.00   4,280,000.00   6,610,000.00   1,400,000.00   18,180,000.00   fighting       1,840,000.00   1,340,000.00   750,000.00     540,000.00     4,470,000.00    adventure      950,000.00     1,320,000.00   1,180,000.00   370,000.00     3,820,000.00    platform       1,290,000.00   1,390,000.00   110,000.00     440,000.00     3,230,000.00    racing         730,000.00     1,770,000.00   10,000.00      280,000.00     2,790,000.00    misc           760,000.00     660,000.00     1,040,000.00   140,000.00     2,600,000.00    simulation     160,000.00     1,270,000.00   330,000.00     130,000.00     1,890,000.00    strategy       240,000.00     590,000.00     230,000.00     70,000.00      1,130,000.00    puzzle         0.00           10,000.00      0.00           0.00           10,000.00

Total Sales                                                                129,940,000.00

Do you want to plot (y/n)? n




Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 5




Thanks for using the program!

I’ll leave you with this: “All your base are belong to us!”




<strong>Test Case 4: </strong>




Enter filename: video_game_sales_2016.csv




Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 1




Enter year: 1999




Video Game Sales in 1999

Name                          Platform  Genre               Publisher                     Global Sales nfl 2k                        dc        sports              sega                          1,190,000.00 shenmue                       dc        adventure           sega                          1,180,000.00 seaman                        dc        simulation          sega                          520,000.00   sega rally championship 2     dc        racing              sega                          410,000.00   j-league pro soccer club      dc        sports              sega                          360,000.00   soulcalibur                   dc        fighting            namco bandai games            340,000.00   virtua striker 2              dc        sports              sega                          320,000.00   pro yakyuu team o tsukuro     dc        sports              sega                          230,000.00   tokyo xtreme racer            dc        racing              genki                         170,000.00   the king of fighters: dre     dc        fighting            snk                           100,000.00   blue stinger                  dc        adventure           activision                    100,000.00   marvel vs. capcom: clash      dc        fighting            capcom                        100,000.00

<h1>(To many titles to show in this document! See Mimir test for full view or “output4.txt”)</h1>







builder’s block               ps        strategy            eon digital entertainment     10,000.00    samurai shodown: warrios      ps        fighting            snk                           10,000.00    derby stallion                sat       sports              ascii entertainment           90,000.00    fire emblem: thracia 776      snes      strategy            nintendo                      260,000.00   digimon adventure: anode      ws        role-playing        namco bandai games            280,000.00   chocobo no fushigi dungeo     ws        role-playing        namco bandai games            180,000.00

Total Sales                                                                               251,110,000.00

Do you want to plot (y/n)? y










Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 2




Enter platform: gen




Video Game Sales for gen

Name                          Year      Genre               Publisher                     Global Sales streets of rage               1990      action              sega                          2,600,000.00 sonic the hedgehog            1991      platform            sega                          4,330,000.00 sonic the hedgehog 2          1992      platform            sega                          6,020,000.00 mortal kombat                 1992      fighting            arena entertainment           2,670,000.00 nba jam                       1992      sports              arena entertainment           2,050,000.00 street fighter ii’: speci     1992      fighting            sega                          1,650,000.00 gunstar heroes                1992      shooter             sega                          130,000.00   ecco the dolphin              1992      adventure           sega                          120,000.00   shining force ii              1993      strategy            sega                          190,000.00   super street fighter ii       1993      fighting            capcom                        150,000.00   ecco: the tides of time       1993      adventure           sega                          70,000.00    street fighter ii’: speci     1993      action              capcom                        70,000.00    streets of rage 3             1993      action              sega                          70,000.00    dynamite headdy               1993      platform            sega                          50,000.00    beyond oasis                  1993      role-playing        sega                          50,000.00    sonic &amp; knuckles              1994      platform            sega                          1,820,000.00 sonic the hedgehog 3          1994      platform            sega                          1,760,000.00 disney’s the lion king        1994      platform            virgin interactive            1,420,000.00 mortal kombat 3               1994      fighting            acclaim entertainment         1,340,000.00 nba jam tournament editio     1994      sports              acclaim entertainment         1,120,000.00 virtua racing                 1994      racing              sega                          260,000.00   lunar 2: eternal blue(sal     1994      role-playing        game arts                     140,000.00   yuu yuu hakusho: makyo to     1994      fighting            sega                          80,000.00    dragon slayer: the legend     1994      role-playing        sega                          80,000.00    j-league pro striker 2        1994      sports              sega                          40,000.00    castlevania bloodlines        1994      platform            konami digital entertainm     40,000.00    puzzle &amp; action: tant-r       1994      misc                sega                          30,000.00

Total Sales                                                                               28,350,000.00

Do you want to plot (y/n)? y










Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher 5) Quit</li>

</ul>




Enter choice: 3




Enter year: 2016




Regional Video Games Sales per Genre

Genre          North America  Europe         Japan          Other          Global          shooter        16,240,000.00  15,900,000.00  1,060,000.00   5,020,000.00   38,220,000.00   action         9,290,000.00   10,680,000.00  7,070,000.00   3,070,000.00   30,110,000.00   sports         7,540,000.00   12,010,000.00  920,000.00     3,020,000.00   23,490,000.00   role-playing   5,890,000.00   4,280,000.00   6,610,000.00   1,400,000.00   18,180,000.00   fighting       1,840,000.00   1,340,000.00   750,000.00     540,000.00     4,470,000.00    adventure      950,000.00     1,320,000.00   1,180,000.00   370,000.00     3,820,000.00    platform       1,290,000.00   1,390,000.00   110,000.00     440,000.00     3,230,000.00    racing         730,000.00     1,770,000.00   10,000.00      280,000.00     2,790,000.00    misc           760,000.00     660,000.00     1,040,000.00   140,000.00     2,600,000.00    simulation     160,000.00     1,270,000.00   330,000.00     130,000.00     1,890,000.00    strategy       240,000.00     590,000.00     230,000.00     70,000.00      1,130,000.00    puzzle         0.00           10,000.00      0.00           0.00           10,000.00




Total Sales                                                                129,940,000.00




Do you want to plot (y/n)? y










Menu options




<ul>

 <li>View data by year</li>

 <li>View data by platform</li>

 <li>View yearly regional sales by genre</li>

 <li>View sales by publisher   5) Quit</li>

</ul>




Enter choice: 5




Thanks for using the program!

I’ll leave you with this: “All your base are belong to us!”




<h1>Grading Rubrics</h1>




Computer Project #08                                   Scoring

Summary




General Requirements:

__0__   (5 pts) Coding Standard 1-9

(descriptive comments, function headers, etc…)




Implementation:

(4 pts) open_file (No Mimir Test)

-2 points No try/except

-2 points No while loop




(6 pts) read_file function test




(5 pts) get_data_by_column function test




(5 pts) get_genre_data function test




(4 pts) get_publisher_data function test




(4 pts) get_totals function test




(4 pts) prepare_pie function test




(3 pts) Pass Test1




(5 pts) Pass Test2




(7 pts) Pass Test3




(3 pts) Pass Test4







Note: hard coding an answer earns zero points for the whole

project

-10 points for not using main()