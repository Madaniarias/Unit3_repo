# QUIZ033
# CODE

```.py
#Write the function mystery and pass the test contained in the file test_quiz_33.py

# The function takes two lists, list1 and list 2, as input and creates an empty list called output.
# It then iterates over the elements of list1 using a loop, and for each element,
# it iterates over the elements of list2 using another loop.
# For each pair of elements, the function checks if the two elements are equal.
# If they are, it adss the element from list1 to the output list.
# After both loops have completed, the function returns the output.


def mystery(list1,list2):
    output = []
    for letter in list1:
        for item in list2:
            if letter == item:
                output.append(letter)

    return output

```
# TEST

![Screen Shot 2023-01-10 at 10 04 53](https://user-images.githubusercontent.com/111761417/211438710-684d0808-bd97-47d1-8bae-33d8d8f8545b.png)

