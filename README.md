# UFOS
# JavaScript, Bootstrap, and UFOs
## Overview of Project
> Dana’s webpage and dynamic table are working as intended, but she’d like to provide a more in-depth analysis of UFO sightings by allowing users to filter for multiple criteria at the same time. In addition to the date, you’ll add table filters for the city, state, country, and shape. 

1. ***Deliverable 1***: Filter UFO sightings on multiple criteria
2. ***Deliverable 2***: A written report on the UFO analysis [`README.md`](https://github.com/emmanuelmartinezs/UFOs). 


# Deliverable 1:  
## Filter UFO sightings on multiple criteria
### Deliverable Requirements:
Using JavaScript and HTML, you’ll modify the code in your `index.html` file to create more table filters. In addition to the date filter you created in this module, you’ll add filters for the city, state, country, and shape, as shown in the following image:

![name-of-you-image](https://github.com/emmanuelmartinezs/UFOs/blob/main/Resources/Images/s1.png?raw=true)

Using JavaScript, you’ll replace the handleClick() function in your app.js file with a new function that saves the element, value, and id of the filter that was changed. Then, you’ll create a new function to loop through the dataset and keep only the results that match the search criteria. The webpage will be updated with the search criteria after pressing "Enter".


1. The list element that creates the button is removed, and there are five list elements for filtering in the `index.html` file. 
2. The event listener is modified to detect changes to each filter in the `app.js` file.
3. ​The `updateFilters()` function saves the element, value, and the id of the filter that was changed.
4. The filterTable() function loops through all of the filters and keeps any data that matches the filter values.
5. The webpage filters the table correctly based on user input.

 
### Results with detail analysis:

1. **The list element that creates the button is removed, and there are five list elements for filtering in the `index.html` file.**


> Image with `JavaScript` & `HTML` Code below.

**Code and Image**


````html
    <!--Filter and Table-->
    <div class="container-fluid">
        <div class="row">
          <div class="col-md-3">
                <form class="bg-dark">
                    <p>Filter Search</p>
                    <ul class="bg-dark">

                        <!-- CHALLENGE NEED - Filter Using New <form> Tag-->
                        <li class="list-group" class="btn-dark">
                                <label for="date">Enter Date</label>
                                <input type="text" placeholder="1/10/2010" id="datetime" />
                        </li>

                        <li class="list-group" class="btn-dark">
                            <label for="city">Enter City</label>
                            <input type="text" placeholder="benton" id="city">
                        </li>

                        <li class="list-group" class="btn-dark">
                            <label for="state">Enter State</label>
                            <input type="text" placeholder="ar" id="state">
                        </li>

                        <li class="list-group" class="btn-dark">
                            <label for="country">Enter Country</label>
                            <input type="text" placeholder="us" id="country">
                        </li>

                        <li class="list-group" class="btn-dark">
                            <label for="shape">Enter Shape</label>
                            <input type="text" placeholder="circle" id="shape">
                        </li>

                    </ul>
                </form>
          </div>


          <!--Dynamic Table-->
          <div class="col-md-9">
                <table class="table table-striped">
                <thead>
                        <tr>
                            <th>Date</th>
                            <th>City</th>
                            <th>State</th>
                            <th>Country</th>
                            <th>Shape</th>
                            <th>Duration</th>
                            <th>Comments</th>
                        </tr>
                </thead>
                <tbody></tbody>
                </table>
          </div>
````

![name-of-you-image](https://github.com/emmanuelmartinezs/UFOs/blob/main/Resources/Images/1.1.JPG?raw=true)



2. **The event listener is modified to detect changes to each filter in the `app.js` file.**


> Image with `JavaScript` & `HTML` Code below.

**Code and Image**


````java
// 1. Create a variable to keep track of all the filters as an object.
var filters = {};

// 3. Use this function to update the filters. 
function updateFilters() {

    // 4a. Save the element that was changed as a variable.
    let inputElement = d3.select(this);
````

![name-of-you-image](https://github.com/emmanuelmartinezs/UFOs/blob/main/Resources/Images/1.2.JPG?raw=true)



3. ​**The `updateFilters()` function saves the element, value, and the id of the filter that was changed.**


> Image with `JavaScript` & `HTML` Code below.

**Code and Image**


````java
function updateFilters() {

    // 4a. Save the element that was changed as a variable.
    let inputElement = d3.select(this);

    // 4b. Save the value that was changed as a variable.
    let inputValue = inputElement.property("value");

    // 4c. Save the id of the filter that was changed as a variable.
    let inputID = inputElement.attr("id");
````





4. **The `filterTable()` function loops through all of the filters and keeps any data that matches the filter values.**


> Image with `JavaScript` & `HTML` Code below.

**Code and Image**


````java
    // 5. If a filter value was entered then add that filterId and value
    // to the filters list. Otherwise, clear that filter from the filters object.

        if (inputValue) {
            filters[inputID] = inputValue;
        } else{filters ={};};
 
  
    // 6. Call function to apply all filters and rebuild the table
    filterTable(filters);
  
  }
````





5. **The webpage filters the table correctly based on user input.**


> Image with `JavaScript` & `HTML` Code below.

**Code and Image**


````java
  // 7. Use this function to filter the table when data is entered.
  function filterTable() {
  
    // 8. Set the filtered data to the tableData.
    let filteredData = tableData;
  
    // 9. Loop through all of the filters and keep any data that
    // matches the filter values
    Object.entries(obj).forEach(([fkey, fval]) =>{
        
      filteredData = filteredData.filter((row) => row[fkey] === fval)
          

  });  
  
    // 10. Finally, rebuild the table using the filtered data
    buildTable(filteredData); 
  }
````





# Deliverable 2: 
## A written report on the UFO analysis
### Deliverable Requirements:
For your written analysis, be sure to use complete and coherent sentences. Your written analysis should contain three sections, which cover the following:

1. **Overview of Project:** Explain the purpose of this analysis. 
2. **Results:** Describe to Dana how someone might use the new webpage by walking her through the process of using the search criteria. Use images of your webpage during the filtering process to support your explanation.
3. **​Summary:** In a summary statement, describe one drawback of this new design and two recommendations for further development.


 
### Results with detail analysis:


1. **Overview of Project:** Our UFOs Project has a single mission, and is to enhance our webpage with capability adding filters with multiple factors.
D3 functionality makes an instance listener for multiple changes in our search, displaying needed datasets on the result table.

> Image with `JavaScript` & `HTML` Code below.

**Code and Image**


````java
// EXTRA: Create a variable to keep track of all the filters as an object.
var clearEntries = d3.select("#clear-btn");
clearEntries.on("click", function() {
  location.reload();
});



// 1. Create a variable to keep track of all the filters as an object.
var filters = {
};

// 3. Use this function to update the filters. 
function updateFilters() {

    // 4a. Save the element that was changed as a variable.
    let inputElement = d3.select(this);

    // 4b. Save the value that was changed as a variable.
    let inputValue = inputElement.property("value");

    // 4c. Save the id of the filter that was changed as a variable.
    let inputID = inputElement.attr("id");
  
    // 5. If a filter value was entered then add that filterId and value
    // to the filters list. Otherwise, clear that filter from the filters object.

      if (inputValue) {
        filters[inputID] = inputValue;
    } else{filters ={};};
  
  
    // 6. Call function to apply all filters and rebuild the table
    filterTable(filters);
};

// 7. Use this function to filter the table when data is entered.
function filterTable(obj) {
  
    // 8. Set the filtered data to the tableData.
    let filteredData = tableData;
  
    // 9. Loop through all of the filters and keep any data that
    // matches the filter values
    Object.entries(obj).forEach(([fkey, fval]) =>{
        
      filteredData = filteredData.filter((row) => row[fkey] === fval)
          

  });
  
    // 10. Finally, rebuild the table using the filtered data
    buildTable(filteredData);
};
  
  // 2. Attach an event to listen for changes to each filter
  d3.selectAll("input").on("change",updateFilters);
  
  // Build the table when the page loads
  buildTable(tableData);
````




2. **Results:** Let’s describe step by step how someone might use the new webpage by walking through the process of using the search criteria. Using images of your webpage during the filtering process to support your explanation.
 
Let’s begin reviewing our HTML Filter and Table code. 

> Image with `JavaScript` & `HTML` Code below.

**Code and Image**


````html
    <!--Filter and Table-->
    <div class="container-fluid">
        <div class="row">
          <div class="col-md-3">
                <form class="bg-dark">
                    <p><b><u>FILTER SEARCH</u></b></p>
                    <ul class="bg-dark">

                        <!-- CHALLENGE NEED - Filter Using New <form> Tag-->
                        <li class="list-group" class="btn-dark">
                                <label for="datetime">Enter Date</label>
                                <input type="text" placeholder="1/10/2010" id="datetime" />
                        </li>

                        <li class="list-group" class="btn-dark">
                            <label for="city">Enter City</label>
                            <input type="text" placeholder="benton" id="city">
                        </li>

                        <li class="list-group" class="btn-dark">
                            <label for="state">Enter State</label>
                            <input type="text" placeholder="ar" id="state">
                        </li>

                        <li class="list-group" class="btn-dark">
                            <label for="country">Enter Country</label>
                            <input type="text" placeholder="us" id="country">
                        </li>

                        <li class="list-group" class="btn-dark">
                            <label for="shape">Enter Shape</label>
                            <input type="text" placeholder="circle" id="shape">
                        </li>
                        
                        <li class="list-group" class="btn-dark">
                            <button id="filter-btn" type="button" class="btn-dark">
                            Filter Table
                            </button>

                            <button id="clear-btn" type="button" class="btn-dark">
                            Clear Table
                            </button>

                        </li>

                    </ul>
                </form>
          </div>
````

From our Website (Project Example:) [`https://www.UFOs.gov`](https://emmanuelmartinezs.github.io/UFOs/). 


![name-of-you-image](https://github.com/emmanuelmartinezs/UFOs/blob/main/Resources/Images/W1.JPG?raw=true)

Need to visit FILTER SEARCH 

![name-of-you-image](https://github.com/emmanuelmartinezs/UFOs/blob/main/Resources/Images/W2.JPG?raw=true)

On filter criteria, you can search by "Shape" only if want, example: triangle

![name-of-you-image](https://github.com/emmanuelmartinezs/UFOs/blob/main/Resources/Images/W3.JPG?raw=true)

And click on "Filter Table" button,

![name-of-you-image](https://github.com/emmanuelmartinezs/UFOs/blob/main/Resources/Images/W4.JPG?raw=true)

Automatically your search criteria will appear in our dynamic table resource.  

![name-of-you-image](https://github.com/emmanuelmartinezs/UFOs/blob/main/Resources/Images/W5.JPG?raw=true)

And, if want to start a new search, just click on "Clear Table" button, and start a new search.

![name-of-you-image](https://github.com/emmanuelmartinezs/UFOs/blob/main/Resources/Images/W6.JPG?raw=true)

After clear table, you may see our default data, 

![name-of-you-image](https://github.com/emmanuelmartinezs/UFOs/blob/main/Resources/Images/W7.JPG?raw=true)




