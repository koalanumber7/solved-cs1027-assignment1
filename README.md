Download Link: https://assignmentchef.com/product/solved-cs1027-assignment1
<br>
To gain experience with

<ul>

 <li>Creating classes with simple methods</li>

 <li>Using linear arrays and multi-dimensional arrays</li>

 <li>Algorithm design</li>

</ul>

<h1>Introduction</h1>

It is important in Computer Science to consider memory and to use compression to reduce the amount of memory being used by a program. A matrix in linear algebra is considered <em>symmetric</em> if it is identical to its transpose. In other words, the element at (i,j) is the same as the element at (j,i) for all i and j in the bounds of the matrix. The <em>diagonal</em> (the set of elements from the top-left corner to the bottom-right corner) is the reflection line. We can represent a matrix as a 2D array in Java and consider the array to be symmetric by the same definition as that of a matrix. For the purpose of reducing memory, we can cut out a roughly half the array since the elements are already stored in the other half of the array.

If we calculate the distances between various locations, a matrix or 2D array can be used to store the distances. For a set of n cities, the array would have n rows and n columns to contain all the distances between each pair of cities. However, this would be an example of a symmetric array since the distance between A and B is the same as the distance between B and A, and thus that distance would exist twice in the array. Similarly, the diagonal of the array would contain all zeroes since the distance between a city and itself is always 0. Due to these observations, we can compress the distance array by storing just the lower-left corner (all the elements below and to the left of the diagonal) rather than the entire array. This compressed array will still contain all the information needed to represent the distance between every pair of cities, but will not contain any unnecessary or redundant data. The Figures below help illustrate this concept more clearly.







Figure 1. An example of a map of 3 cities, A, B, and C, and the distances between them.




Figure 2. A matrix (2D array) representing the distances between each of the cities from the map in Figure 1 above.










Figure 3. Another example of a matrix (2D array) containing hypothetical distances between cities or objects (left), and the CompressedArray of the same matrix (right).




Assume an “original” 2D array has n by n elements. When compressing this into a

CompressedArray structure, we want to only include the elements that are below and to the left of the diagonal, as illustrated in Figure 3. To determine the number of elements needed in the CompressedArray, take the number of the elements in the original array, and subtract the number of elements on the diagonal (this is also n) to determine the number of non-diagonal elements. However, this number also include the top-right triangle which should also be cut out. Divide this number by 2 to determine the number of elements in the lower-left triangle only.




<h1>Provided files</h1>




The following is a list of files provided to you for this assignment. Please do not alter these files in any way.

<ul>

 <li>java – adds a city marker icon on the visual GUI</li>

 <li>java – provides a visual GUI for the program</li>

 <li>java – reads in text files</li>

 <li>java – tests that CompressedArray is working  TestProgram.java – tests that Program is working</li>

</ul>




<h1>Classes to implement</h1>




For this assignment, you must implement 3 Java classes: <em>City</em>, <em>CompressedArray</em>, and <em>Program</em>. Follow the guidelines for each one below.

In all of these classes, you can implement more private (helper) methods, if you want to, but you may<strong> not</strong> implement more public methods. You may<strong> not</strong> add instance variables other than the ones specified below. Penalties will be applied if you implement additional instance variables or change the variable types or modifiers than what is described here.




<h2>City.java</h2>




This class represents each city that is loaded in from a text file. It is a simple class that just contains the city’s name, x and y coordinates, and a CityMarker icon.

The class must have the following <em>private</em> variables:

<ul>

 <li>name (String)</li>

 <li>x (int)</li>

 <li>y (int)</li>

 <li>marker (CityMarker)</li>

</ul>

The class must have the following <em>public</em> methods:

<ul>

 <li>public City(String, int, int) [constructor] o Takes in parameters for name, x, and y and assigns these values to the corresponding instance variables. The marker variable must also be initialized in this constructor as a new CityMarker object.</li>

 <li>public String getName() o Returns name</li>

 <li>public int getX() o Returns x</li>

 <li>public int getY() o Returns y</li>

 <li>public CityMarker getMarker() o Returns marker</li>

 <li>public void setName(String) o Sets name</li>

 <li>public void setX(int) o Sets x</li>

 <li>public void setY(int) o Sets y</li>

 <li>public void setMarker(CityMarker) o Sets marker</li>

 <li>public String toString() o Returns the city name</li>

</ul>




<h2>CompressedArray.java</h2>




This class represents the array that has been compressed from a matrix (2D array) into a linear array that excludes elements from the diagonal and any elements above or to the right of the diagonal. Only elements below or to the left of the matrix diagonal must be included in the CompressedArray.

The class must have the following <em>private</em> variables:

<ul>

 <li>origArraySize (int)</li>

 <li>array (double[])</li>

</ul>

The class must have the following <em>public</em> methods:

<ul>

 <li>public CompressedArray(double[][]) [constructor] o Takes in a 2D double array (double[][]) which represents the “original array” o Initialize the linear double array (instance variable array) and copy the elements from the original array into this linear array so that it contains only the lower-left triangle elements of the original array (the elements to the left and below the</li>

</ul>

diagonal). The elements from this triangle must be added to the CompressedArray in order from left to right and top to bottom. o Hint: Read the description near the top of this document to determine the required capacity for this CompressedArray.

<ul>

 <li>public int getLength() o Returns the length of the new, compressed array</li>

 <li>public double getElement(int) o Returns the element in the new, compressed array stored at the given index</li>

 <li>public boolean equals(CompressedArray) o Checks equality between the two CompressedArray objects by checking if they have the same length and that all the elements are identical in the same order</li>

 <li>public String toString() o Builds a string that contains the CompressedArray and formats it in a trianglular structure to look like the lower left corner of a matrix. Each element should take up exactly 8 characters and show 2 decimal places. o Hint: Use String.format(“%8.2f”, element) for each element and remember to add a newline at the correct places</li>

</ul>




<h2>Program.java</h2>




This class, as its name suggests, will be the main heart of the program. It will be the entry point of the program, read in a file of cities and create objects for each of them, contain the array of those cities, and create a CompressedArray containing the distances between each of the cities read in from the file.

The class must have the following <em>private</em> variables:

<ul>

 <li>cityCount (int)</li>

 <li>cityArray (City[])</li>

 <li>array (CompressedArray)</li>

</ul>

The class must have the following methods:

<ul>

 <li>public Program(String, boolean) [constructor] o Takes in a String representing the file to load (i.e. “cities1.txt”) and a boolean</li>

</ul>

(showMap) that indicates whether or not the map GUI should be displayed o Initialize cityArray with 3 cells

<ul>

 <li>Create an object of MyFileReader or use your own code to read in a text file, and load in the file with the given name.</li>

 <li>Read in each line from the file and create a City object containing the city name, and the x and y values from the file (look at the text file to see this format). Add the city object to the cityArray and expand the capacity if needed. o If the boolean (showMap) is true, then create a Map object and call addCity() on the Map object for each city in the cityArray. This will add the marker icons to the map for each city.</li>

</ul>

<ul>

 <li>public City[] getCityList() o Returns cityArray</li>

 <li>private void expandCapacity() o Expands the capacity of cityArray by adding 3 additional slots to the array</li>

 <li>public double distBetweenCities(City,City) o Calculates the Euclidean distance between the two given Cities</li>

 <li>public void compareDistances() o Create a 2D double array (i.e. double[][]) with a size of N by N, where N is the number of cities in cityArray. Loop through every combination of pairs of cities and call distBetweenCities() for each pair. Save this result into the double[][] array in the appropriate cell.</li>

 <li>public CompressedArray getArray() o Returns array</li>

</ul>


