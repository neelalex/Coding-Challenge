![eBayK Logo](https://www.ebay-kleinanzeigen.de/static/img/common/logo/logo-ebayk-402x80.png)
# SQL Coding Challenge

Congratulations! You made it to the eBay Kleinanzeigen remote SQL Coding Challenge, where we want to see your hands-on coding skills.


## Steps

1. Check installation prerequisites: JDK version >=11, Maven latest version, your preferred IDE/editor. To see that everything basic is working, execute `mvn verify`, it should show you a `SUCCESS` build.
2. Read carefully through "Requirements" and "Out-of-scope" to focus on the right things.
3. IMPORTANT: After finishing coding, please add your comments and remarks inside this `README.md` file, see end of file. It helps us gaining context on how you reflect on the coding task.
4. Send back the result as mentioned inside the coding challenge mail

Coding guidance: Combine "clean, object-oriented, tested code" with "working software".


##  Requirements

* Read and parse data from [`purchases.csv`](/src/main/resources/purchases.csv) and [`users.csv`](/src/main/resources/users.csv) and initialize to [`Table.java`](/src/main/java/exercise/Table.java)
* [`Table.java`](/src/main/java/exercise/Table.java) should be generic, column-names are inside .csv files and parsing should be based on this source.
* Implement an ORDER BY DESC ([SQL reference](http://www.w3schools.com/sql/sql_orderby.asp))
  * Input: 
    * the name of the column to order the rows
  * Output: the ordered table
* Implement an INNER JOIN of two tables ([SQL reference](https://www.w3schools.com/sql/sql_join.asp))
  * Input:
    * the name of the column to use for the join from the right table
    * the name of the column to use for the join from the left table
  * Output: the joined table
* Structure and design [`Table.java`](/src/main/java/exercise/Table.java)
  * Think about an appropriated domain model. Hint: the domain should not be purchases and users.
* You are not restricted to implement everything in the existing file/folder structure. Feel free to add or alter files as you see fit.


## Out-of-scope

* NO "real" persistence necessary (do not integrate MySQL, HSQLDB, h2database, or JPA). Use your own internal storage model (see also [`Table.java`](/src/main/java/exercise/Table.java)).
* NO need to implement any SQL parser or anything, Java code interface is sufficient.
* NO need to be Maven expert or adapt build, project harness and build is setup already.
* NO Javadoc necessary. Tests and self explaining code are sufficient.


## Your comments / remarks

What would you do if you had more time? Which design decisions and trade-offs did you take?

My answer:
I would have tried to create a system where the Tables are created in dynamic based on the first record present in the csv file.
This can be achieved by using 

public class CSVTable {
    private String[][] csvTable = null;
    public CSVTable(int columns) {
        csvTable = new String[columns][2];
    }
    public String[][] getCSVTable() {
        return this.csvTable;
    }
    public void setCSVTable(String[][] csvTable){
        this.csvTable = csvTable;
    }
}

CSV parser:
    while(iterator.hasNext()){
        record = iterator.next();
        CSVTable csvTable = new CSVTable(record.length);
        String[][] insertRecord = csvTable.getCSVTable();
        for(int i = 0; i < length; i++){
                insertRecord[i][0] = columns[i];
                insertRecord[i][1] = record[i];
        }
        csvTable.setCSVTable(insertRecord);
        csvObjects.add(csvTable);
    }

I found this approach via searching over internet, hence not implementing here as this is something I didn't know before hand.

If I had more time. I would have definitely learned and implemented the above approach to make our code generic.


Remaining, I need to clean the structure of the code, by segregating Entity objects, into a group.

Added some unwanted dependencies to POM file. need to clean that up.

Have fun!


User to add 1 to *
