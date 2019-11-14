# project2
<h6>PROJECT 2 <H6>
In a file named "project.cpp", you need to write a program that prompts the user to provide a password, and then print out the common passwords most similar to the password the user provided.

Each test case has a file named "common_passwords.txt", this file consists of the 1000 most common passwords. You can assume **no password contains whitespace.**

However, some of the passwords are quite offensive: so here is my redacted file (the test cases don't involve any of the offensive terms): common_passwords.txt

This file was *modified* from: https://github.com/DavidWittman/wpxmlrpcbrute/blob/master/wordlists/1000-most-common-passwords.txt

 

Example program execution (bold is user input):

Give me a password: josh
You provided a password of josh
The most similar passwords to josh are:
fish, john, joshua,
All of which are 2 character(s) different.

In the 1000 most common passwords, "josh" doesn't appear, nor does any word that is one character different from it. But there are three words that are 2 characters separated from "josh", and those are "fish", "john", and "joshua". When calculating distance between words, just compare characters at the same position (no fancy shifting needed).
