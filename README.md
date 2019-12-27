# Syft Git Search App

![alt text](https://github.com/shaon007/Syftapp_kotlin_mvvm/blob/master/app/src/main/res/drawable/screenshot_syftapp.JPG)

The app generates search results in the form of a list as the user types in text into the search field.
There is an additional filter function next to the search box, this opens a dialog with the options to filter results by topic and language categories.
A total count of the search result is shown below the search field.
The results are sorted by the order of their star rating from high to low. The results display git name, language followed by a truncated description.
Technologies implemented
•	Kotlin - This is my second implementation in Kotlin. I am still in the process of learning the language as I want to cross over to Kotlin entirely for Android development.
•	MVVM pattern
•	Dagger 2
•	Retrofit
•	Infinite scrolling mechanism
•	Unit test, mockito

Development brief
In order to search git repositories whenever user types anything in searchbox, I needed to make api call every time a character is entered and cancel the previous api calls made already.
First attempt was to use RxJava for api calls and dispose previous results but it was making all the api calls for each search character entered and fetching random results.
I used switchMap with LiveData as parameter instead. Now as text is changed in search box,  switchMap acts only on that latest text. But then again there was a problem of the API for calling it too fast every time a character was entered, so I delayed each api call for 2 seconds.
I wanted to filter from just the search results but couldn’t find the fields to filter on. So I had to make new api calls to filter by topic and language. If I could have stored the result in local database then it would have been faster to run the filter.
I have spent roughly 2 days to develop this, a large chunk of my time was spent in trouble shooting my first attempt. It took me a bit of time to write the  test codes as I haven’t had to do many in the past.


Testing
As this is the search app, I focused my tests on making sure search entries don’t return errors on mistakes like whitespaces and calls correct methods for api calls and results. I have also used a generic class for handling any error or empty results.
I have used unit testing with Mockito. Here is a breakdown of the tests I have written so far:
•	If no character or whitespace is entered in search then the api call result isn’t observed
•	If no character or whitespace is entered in search then the method for api call isn’t called
•	If success result is turned from api call then the result can be observed with LiveData
•	If any text is entered in  search box then correct method is being called 
•	If somehow empty search query is submitted for api calls then it throws exception



## Built With

Using the Github API

https://developer.github.com/v3/search/#search-repositories



## Author

* **Rashedul Hasan**  



