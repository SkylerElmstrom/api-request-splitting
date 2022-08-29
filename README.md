# Splitting API GET requests into multiple processes
API requests, especially larger ones, might beenfit from running multiple smaller requests in parallel versus large requests in series. While this is arguably a questionable method that will quickly rack up your count towards a rate limit, I find myself needing faster information more than I exceed my current generous rate limits with the APIs I utilize.

Splitting an API request into multiple process will require these steps:

- I need to create a function that will 'split' an API URL into smaller 'requests' i.e. if I am pulling data from an API for 1 year, perhaps I'd like to split this request into smaller ones for each month.
- I need a method of assigning 'worker' processes each split of my URL and the code to fetch their data
- I need a method that tracks existing 'workers' and their progress
- I need a method to wrap up the joining of the data once all the 'workers' have completed their tasksw

## Resources that I've found helpful

### Synchronous vs Asyncronous programming
A primer from Winston Change at rstudio:conf 2020:
https://www.rstudio.com/resources/rstudioconf-2020/asynchronous-programming-in-r/

### Callr and multiple background processes

Info on `callr`:\
https://callr.r-lib.org/#multiple-background-r-processes-and-poll

Tidyverse blog on creating a task que using `callr`:\
https://www.tidyverse.org/blog/2019/09/callr-task-q/

Important primer on R6 objects and OOP:\
https://adv-r.hadley.nz/r6.html
https://r6.r-lib.org/

