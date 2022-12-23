HIGH LEVEL APPROACH:

The Web Crawler first logs into facebook.  It does this by sending a get request for the necessary log-in tokens.  To login, a post request is sent containing the login info from the input. (username and password.) After login the anchor tag in the HTML is found, and the buffered URL is stored in a list (global variable with list of buffers.) . As the urls are traversed through, using http_send, I search for flags, and store the urls visited in a global variable. When responses from the server are recieved, the status codes are handled by parse_stat_code.  If the code is 200, the response is returned, if 503, try again, 302 new url, etc.  I used threads to run exec_crawl on 5 instances of HTMLParser, each finding one of the secret flags.  HTMLParser is defined as its own class, as well as WebCrawler for the crawler itself.  The command line arguments are handles when main is executed.

CHALLENGES:

One of the challenges I faced was figuring out how to get the facebook login working, and how exactly to send those messages.  Another challenge I faced was deciding how to find the flags simoultaneously without the program taking excessively long, I did this by using threads as I stated above. Everything else was relatively trivial in this particular project. 

TESTING:

I mainly tested this project by submitting the project throughout to gradescope and seeing what was required, and also printing status messages in each method as I created them (I deleted them to cleanup the code for final submission. ) I would print data such as how many urls I visited, messages recieved and sent, etc.

