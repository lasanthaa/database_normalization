# Normalization in dbms

### Why normalization

---

Normalization is a process of organizing the data in database to avoid data redundancy. Redundancy mean duplication of same data in dbms.

---

### Anomalies in DBMS

---

There are three types of anomalies that occur when the database is not normalized.These are Insertion, update and deletion anomaly. To overcome these anomalies we need to normalize the data.


Here are the most commonly used normal forms:

---

##### First normal form(1NF)
##### Second normal form(2NF)
##### Third normal form(3NF)
##### Boyce & Codd normal form (BCNF)

---

### First normal form (1NF) --->  Atomicity 

Column (attribute) of a table cannot hold multiple values. ( should be atomic )

##### example 

|Customer table |
|---------------| 


| customer_id        | firstname           | surname  | tp
| ------------- |:-------------:| :-----:| :-------:     
| 123     | Pooja |  Singh | 555-861-2025, 192-122-1111              
| 234      | San      |   Zhang | (555) 403-1659 Ext. 53; 182-929-2929
| 456 |  John      |   Doe |  555-808-963

Note that tp column contain more than one number for one customer.
So apparent solution can be adding more columns.

| customer_id        | firstname           | surname  | tp | tp2
| ------------- |:-------------:| :-----:| :-------:  | :---: 
|  
| 123     | Pooja |  Singh | 555-861-202 | 192-122-1111              
| 234      | San      |   Zhang | (555) 403-1659 | Ext. 53; 182-929-2929| 
| 456 |  John      |   Doe |  555-808-963


Technically, this table does not violate the requirement for values to be atomic. However, informally, the two telephone number columns still form a `repeating group`  they repeat what is conceptually the same `attribute`, namely a telephone number. An arbitrary and hence meaningless ordering has been introduced


To bring the model into the first normal form, we split the strings we used to hold our telephone number information into "atomic" entities: single phone numbers. And we ensure no row contains more than one phone number.


| customer_id        | firstname           | surname  | tp
| ------------- |:-------------:| :-----:| :-------:     
| 123     | Pooja |  Singh | 555-861-2025, 192-122-1111   
| 123     | Pooja |  Singh | 192-122-1111               
| 234      | San      |   Zhang | (555) 403-1659 Ext. 53 1
| 234      | San      |   Zhang | 82-929-29291
| 456 |  John      |   Doe |  555-808-963