Hello!!

Welcome to the best trivia game!! (Probably isn't)

There are no special instructions

My design decisions are based on a simple idea:
		Make the solution as generalized as possible
		
Therefore, if my code is given any set of tests with the same question format, it will be able to handle any number of questions, and any number of tests

Some of the solutions include trying to skirt JavaScript oddities, for example, by writing the entire Html for the radio buttons into the label innerHTML
I could avoid the issue of managing two different elements that rely on each other. While appending the button to the label would work, the text would
appear before the radio button, which made the page look terrible, honestly.

I also decided that the id for each question would be equal to the question number instead of the index number since it improved readability when
inspecting the page, and made it easier for me to debug the code

Each group of radio buttons was given a name that matches its parent question's ID, so its easier to later retrieve and iterate therough them

To randomise the answer order, a random number is generated within the range of answers while iterating through the answers, each answers is placed
in a position based on a comparison between the generated number and the current index. This could probably be replaced by a function to clean up the
code, so I might do that if I have the chance

For check test, I decided to check and remove all possible additions from previous check tests to avoid any unexpected behaviour. This included the
result, and the checks and x's. For the pictures, I thought I could give them a name and then retrieve a collection with them to iterate and remove each
but apparently getElementsByName behaves unexpectedly with images, so instead I gave them all the same id and have a loop that tries to retrieve one, and
if it succeeds in doing so, it then removes it.

For the actual answer checking, I figured it would be more efficient to combine checking if all questions are answered with finding the checked answers 
by creating an array of objects, where each object stores the answer for a question and the position of the answer within its group. The answers are
compared to the correct answer in the same position in the provided test array, and the score is tallied.

Colour changes are done when while retrieving the answers, and picture adding is done while markin the test.

For the randomTest functionality, after the GET request is sent and processed, the function checks if the the response was successful. If it was it adds
the results it received to the tests collection, then calls loadTest. To make sure the previous functions can still be used with randomTest, two edits
were made. loadTest takes an argument, which if true informs it that it should retrieve the newly added random test from tests. The second edit is a
global variable set by loadTest, which checkTest uses to know whether to retrieve the value from the dropdown menu or to get the random value.

There are no added functionalities for now.