# Knn vectors classification
In this project the server can handle several clients at the same time, using multi-threading. 
Each client speaks with a CLI object which plays a role as a "sub server" that deals only with this
specific client requests , based on the input from the user in the client side.
The project contains the following files :
- client.cpp
- server.cpp
- Knn.cpp
- Knn.h
- KnnEuclidean.cpp
- KnnEuclidean.h
- KnnManhattan.cpp 
- KnnManhattan.h
- KnnChebyshev.cpp
- KnnChebyshev.h
- KnnCanberra.cpp
- KnnCanberra.h
- KnnMinkowski.cpp
- KnnMinkowski.h
- FileValidate.cpp
- FileValidate.h
- CLI.cpp
- CLI.H
- Command.cpp
- Command.h
- CommandBegin.cpp
- CommandBegin.h
- Upload.cpp
- Upload.h
- Parameters.cpp
- Parameters.h
- Classification.cpp
- Classification.h
- PreparedVectors.cpp
- PreparedVectors.h
- ResultFile.cpp
- ResultFile.h
- DefaultIO.cpp
- DefaultIO.h
- SocketIO.cpp
- SocketIO.h
- Elements.cpp
- Elements.h
- makefile
###  
# How to compile and run the project
1. Download to your computer all the files that described above and put them in the same directory.
2. Open two terminals in the path of the directory you inserted all the files.
3. Know your path of the csv files you would like to run in the program, you can use the csv files from this repository.
3. Use the following compile line : make 
4. Use the following run line for the server : ./server.out [wanted server port].
   - For example: ./server.out 12345
   - Pay attention that valid ports numbers are in the range of 1024 - 65535.
5. Use the following run line for the client: ./client.out [wanted server ip] [wanted server port].
   - For example: ./client.out 127.0.0.1 12345
   - Pay attention if the client won't insert the matching port of the wanted server he won't connect to the wanted server
     and he will need to start over the run which in this run he will need to run the client with the matching port.
   - If the user will insert invalid ip or inavlid port the program will close and he will need to start over.
6. Another option is to clone the project by using Git and than compile and run the project with the accurate lines in section 4 and section 5.
    - The link for our github is : https://github.com/RoiElitzur/adv_prog_ass4.git.

# About the user's input at the client side
  - Option 1:
       - The user needs to insert two valid paths , the first one will be the one of the classified vectors csv file and the 
         second one will be the one of the unclassified vectors csv file.
       - If one of the paths are invalid or the content of the file are not valid for some reasons such as:
            - Invalid vectors values (only doubles.)
            - Invalid size of one or more classified vectors(all need to be the same size as the size of the first vector in the file).
            - Invalid size of one or more uncalssified vectors (all need to be the same size as the classified vectors).
        Therefore all the data of the previous csv file that inserted (if inserted at all) will be deleted and the user will need to insert
        two valid csv files in order to proceed to the next options.
  - Option 2:
      - The server will send to the client the current values and they will be printed to the screen, the client can leave the current values or enter new                      values. In order not to make a change, the user must press enter, otherwise the user must enter a K followed by a distance metric. If the user enters valid            values, they will be entered as the new values, otherwise no change will be made.
      - Valid values are: 
      - The distance calculate methods you can insert as arguments are:
        - AUC - for Euclidean
        - CAN - for Manhattan
        - CHB - for Chebyshev
        - CAN - for Canberra
        - MIN - for Minkowski
      - k argument value can be maximum the numbers of lines in your csv file and has to be an integer number.
- option 3:
    -The server will perform classification for the test vectors file. If the client request to perform classification occurs before files have been uploaded to the          server, "please upload data" will be printed on the screen. 
- option 4:
    -The server will send to the client the classification of each vector from the of test vectors file. the classifications will be printed to the user's screen.
    - If the client request the classifications before uploading files and asking the server to classify them, an appropriate error message will be printed on the           user's screen.
- option 5:
    - The user has to enter a path to the file to which the classifications for the vectors from the test file will be printed. The server will then send the                 classifications to the client and they will be printed to the necessary file. If the user enters an incorrect path, an error will be printed on the screen and         the classifications will not be sent and written to the file.
    - If the client request the classifications before uploading files and asking the server to classify them, an appropriate error message will be printed on the           user's screen.
    - Pay attention! The path must include the name of the new file where the classifications will be written!
- option 8:
   - The communication between the client and the server will end and the program will close.    
# About the distance functions
In the assignment we wrote 5 types of vectors distance calculating :
- Euclidean distance
- Manhattan distance
- Chebyshev distance
- Canberra distance
- Minkowski distance
###
# Valid input to the project
- The project calculates the distance based on input numbers from the csv files. The valid input is only numbers, input files that contains letters, signs or any other non-digit character will be invalid input and will cuase the files to be invalid.
- In Canberra distance definition there is a constant number p, we used p = 2 and it can be changed easily by changing the #define of p in KnnCanberra.
###
