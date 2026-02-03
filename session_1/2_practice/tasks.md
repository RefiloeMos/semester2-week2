# Library SQL Exercises

## Datetime in SQL

Some of these tasks use datetimes - you can convert a date into the right format using:
```sql
DATE('20-01-2026') /* convert a specific date to a datetime */
DATE('now') /* convert the current time to a datetime */
DATE('now', '-14 days') /* you can add or subtract days */
```


1. **List all loans**  
Show book title, member name, and loan date.
-- 
2. **Books and loans**  
List all books and any loans associated with them.
--SELECT Books.title AS BookTitle, COUNT(Loans.id) AS Loans FROM Books LEFT JOIN Loans ON Books.id = Loans.book_id GROUP BY BookTitle;
3. **Branches and books**  
List all library branches and the books they hold.
SELECT LibraryBranch.name AS LibraryBranch, Books.title AS Books FROM LibraryBranch LEFT JOIN Books ON LibraryBranch.id = Books.branch_id GROUP BY LibraryBranch;
4. **Branch book counts**  
Show each library branch and the number of books it holds.
SELECT LibraryBranch.name AS LibraryBranch, COUNT(Books.title) AS NumberOfBooks FROM LibraryBranch LEFT JOIN Books ON LibraryBranch.id = Books.branch_id GROUP BY LibraryBranch;
5. **Branches with more than 7 books**  
Show branches that hold more than 7 books.
SELECT LibraryBranch.name AS LibraryBranch, COUNT(Books.title) AS NumberOfBooks FROM LibraryBranch LEFT JOIN Books ON LibraryBranch.id = Books.branch_id GROUP BY LibraryBranch HAVING NumberOfBooks > 7;
6. **Members and loans**  
List all members and the number of loans they have made.
SELECT Members.name AS Member, COUNT(Loans.book_id) AS NumberOfLoans FROM Members LEFT JOIN Loans ON Members.id = Loans.member_id GROUP BY Member;
7. **Members who never borrowed**  
Identify members who have never borrowed a book.
SELECT Members.name AS Member, COUNT(Loans.book_id) AS NumberOfLoans FROM Members LEFT JOIN Loans ON Members.id = Loans.member_id GROUP BY Member HAVING NumberOfLoans < 1;
8. **Branch loan totals**  
For each library branch, show the total number of loans for books in that branch.

9. **Members with active loans**  
List members who currently have at least one active loan.

10. **Books and loans report**  
Show all books and all loans, including books that were never loaned. Include a column classifying each row as “Loaned book” or “Unloaned book.”. You will need to look up how to do this (hint: a case statement would work).
