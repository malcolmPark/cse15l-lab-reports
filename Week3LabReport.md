# **Week 2 Lab Report** by Malcolm Park (Jooahn)

This weeks lab report will focus on writing a markdown file on Github about how to create a web server that will keep track of a string value, which
will get added to by the incoming requests from the URL.

## Part 1
The raw Java code is shown below. This code is in the StringServer file.
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String statement = "";
    public String handleRequest(URI url) {
        // If the path is just a slash (/), it will return a string value stating what the String is currently at.
        if (url.getPath().equals("/")) {
            return ("Current String:" + statement);
        // However, if the path contains the statement "/add-message?s=", it will split the path from the =
        // Then, it will get the second part of the path, which will refer to the string value we want to append.
        // Finally, it will return that the statement has been appended.
        } else if (url.getPath().equals("/add-message")) {
            String partsOfQuery[] = url.getQuery().split("=");
            statement += ("\n" + partsOfQuery[1]);
            return "Statement appended!";
        } else {
            return "Server not found!";
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

### Explanation of how the file works. 
> This is web server called StringServer. It has one instance variable of String type called statement.
> When we first load this web server to a localhost, the statement is blank. However, the user can make
> a request to concatenate a new line and then a string to the statement variable, through this format:
> `/add-message?s=<string>`

1. First loading the server to localhost:4000.
- <img width="300" alt="Screen Shot 2023-01-30 at 3 55 09 PM" src="https://user-images.githubusercontent.com/122580137/215623544-7e09227c-7ba9-40d5-b783-9191a4c896b8.png">
- This screenshot shows what happens when we first load the server. Only the words "Current String:" appear because we haven't
appended anything to the string instance variable yet.
2. Using `/add-message?s=Hello, my name is Malcolm`.
- <img width="300" alt="Screen Shot 2023-01-30 at 3 57 33 PM" src="https://user-images.githubusercontent.com/122580137/215623798-b32c2245-e3fd-4540-ba6d-122d6330add3.png">
- When we add the string value "Hello, my name is Malcolm", we see "Statement appended!".
- Now, if we move back to the starting url (http://localhost:4000/) we see that the instance variable has changed.
- <img width="300" alt="Screen Shot 2023-01-30 at 3 59 57 PM" src="https://user-images.githubusercontent.com/122580137/215624128-88999a69-9cd6-4f27-b09b-54dda4c9df6a.png">
3. Using `/add-message?s=I love to code in Java! I wonder what your favorite language is?`.
- Lets see if this works if we append a longer string as well.
- <img width="300" alt="Screen Shot 2023-01-30 at 4 04 00 PM" src="https://user-images.githubusercontent.com/122580137/215624587-ca157608-b12a-4963-90c6-1591832e7b72.png">
- When we add the string value "I love to code in Java! I wonder what your favorite language is?", we again see
"Statement appended!".
- Now if we move back to the starting url again (http://localhost:4000/) we see that the instance variable has changed.
- <img width="300" alt="Screen Shot 2023-01-30 at 4 05 32 PM" src="https://user-images.githubusercontent.com/122580137/215624744-4c74e829-fbbe-4611-9c14-5c214f6c29bb.png">
4. Using `/add-message?s=`
- This will show an edge case that represents a situation where we leave the appending message section blank.
- <img width="300" alt="image" src="https://user-images.githubusercontent.com/122580137/215628224-7c17eb69-aa64-4eba-a006-9551b58794a9.png">
- In this case, it returns "Message not filled" and indicates that the message section of the query is empty. It does not append
anything in this situation.


## Explanation of each screenshot
For both screenshots, the main method creates a URLHandler that manages the string instance variable, and then uses Server.java file
that we used in the lab of Week 2 to start a web server.
1. For the first and second screenshot, when we first load the server we call the method handleRequest. When we load the server, the 
if, else if, and else statements are run to append string values appropriately at the right condtions. The parameter for this
method is the url itself. By running the url of "localhost:4000/add-message?s=Hello, my name is Malcolm" and
"localhost:4000/add-message?s=I love to code in Java! I wonder what your favorite language is?", the method checks if the 
words "add-message" is contained in the url. If there is, the query of the url is split by the = sign, and the elements are 
added into a string array called partsOfQuery. The first element in this array will be "s", and the second element will be
 "Hello, my name is Malcolm", which is then appended to the instance variable statement with a new line (\n).

2. For the third screenshot, it is still the same when we first load the server, we call the method handleRequest. Since there,
 are the words "add-message", it will still pass on to the else if statement, but since the string array partsOfQuery will only
 have a length of one, it returns the statement "Message not filled" and the instance variable is not changed.

## Part 2


