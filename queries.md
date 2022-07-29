  

### Create database named: FacultySystemDB. 

```test> use FacultySystemDB```

switched to db FacultySystemDB
FacultySystemDB> db.createCollection("student")

{ ok: 1 }

#### Create collection (student) that has:
##### •FirstName: string
##### •LastName: string
##### •Age: Number
##### •Faculty: An object that has Name and Address
##### •Grades: An array of objects, each object has: CourseName, Grade, Pass (Boolean).
##### •IsFired: Boolean
 
#### Insert 3 (at least) documents in Student collection with different values.
##### •Try inserting one record each time
##### •Try inserting collection using on insert statement.

```FacultySystemDB> db.student.insert( {FirstName: "John", LastName: "Doe", Age: 20, Faculty: {Name: "Engineering", Address: "123 St"}, Grades: [{CourseName: "Mongodb", Grade: 100, Pass: true}], isFired: false})```

{

acknowledged: true,

insertedIds: { '0': ObjectId("62e3e5d718c926789c103996") }

}

  

```FacultySystemDB> db.student.insert({FirstName: "Jane", LastName: "Doe", Age: 20, Faculty: {Name: "Engineering", Address: "123 St"}, Grades: [{CourseName: "Mongodb", Grade: 100, Pass: true}], isFired: false})```

{

acknowledged: true,

insertedIds: { '0': ObjectId("62e3e5ed18c926789c103997") }

}

  

```FacultySystemDB> db.student.insert({FirstName: "John", LastName: "Smith", Age: 20, Faculty: {Name: "Engineering", Address: "123 St"}, Grades: [{CourseName: "Mongodb", Grade: 100, Pass: true}], isFired: false})```

{

acknowledged: true,

insertedIds: { '0': ObjectId("62e3e60518c926789c103998") }

}

  
  

```FacultySystemDB> db.student.insertMany([{FirstName: "John", LastName: "Does", Age: 20, Faculty: {Name: "Engineering", Address: "123 St"}, Grades: [{CourseName: "Mongodb", Grade: 100, Pass: true}], isFired: false},{FirstName: "Jane", LastName: "Doe", Age: 20, Faculty: {Name: "Engineering", Address: "123 St"}, Grades: [{CourseName: "Mongodb", Grade: 100, Pass: true}], isFired: false}, {FirstName: "John", LastName: "Smith", Age: 20, Faculty: {Name: "Engineering", Address: "123 St"}, Grades: [{CourseName: "Mongodb", Grade: 100, Pass: true}], isFired: false}])```

{

acknowledged: true,

insertedIds: {

'0': ObjectId("62e3e7fa18c926789c103999"),

'1': ObjectId("62e3e7fa18c926789c10399a"),

'2': ObjectId("62e3e7fa18c926789c10399b")

}

}

  

#### Retrieve the following data:
##### All Students.
##### Student with specific First Name.
##### Students who his First Name=Ahmed, or Last Name= Ahmed.
##### Students that their First name isn't "Ahmed".
##### Students with Age less than 21.
##### All fired students.
##### Students with Age more than or equal to 21, and their faculty isn't NULL.
##### Display student with specific First Name, and display his First Name, Last name, IsFired fields only.

```FacultySystemDB> db.student.find()```

[

{

_id: ObjectId("62e3e5d718c926789c103996"),

FirstName: 'John',

LastName: 'Doe',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e5ed18c926789c103997"),

FirstName: 'Jane',

LastName: 'Doe',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e60518c926789c103998"),

FirstName: 'John',

LastName: 'Smith',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e7fa18c926789c103999"),

FirstName: 'John',

LastName: 'Does',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e7fa18c926789c10399a"),

FirstName: 'Jane',

LastName: 'Doe',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e7fa18c926789c10399b"),

FirstName: 'John',

LastName: 'Smith',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

}

]

```FacultySystemDB> db.student.find({FirstName: "Jane"})```

[

{

_id: ObjectId("62e3e5ed18c926789c103997"),

FirstName: 'Jane',

LastName: 'Doe',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e7fa18c926789c10399a"),

FirstName: 'Jane',

LastName: 'Doe',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

}

]

  
  

```FacultySystemDB> db.student.find( {$or: [{FirstName: "Ahmed"},{LastName: "Ahmed"}]})```

  

```FacultySystemDB> db.student.find({FirstName: { $ne: "Ahmed"}})```

[

{

_id: ObjectId("62e3e5d718c926789c103996"),

FirstName: 'John',

LastName: 'Doe',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e5ed18c926789c103997"),

FirstName: 'Jane',

LastName: 'Doe',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e60518c926789c103998"),

FirstName: 'John',

LastName: 'Smith',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e7fa18c926789c103999"),

FirstName: 'John',

LastName: 'Does',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e7fa18c926789c10399a"),

FirstName: 'Jane',

LastName: 'Doe',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e7fa18c926789c10399b"),

FirstName: 'John',

LastName: 'Smith',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

}

]

```FacultySystemDB> db.student.find({Age: {$lt: 21}})```

[

{

_id: ObjectId("62e3e5d718c926789c103996"),

FirstName: 'John',

LastName: 'Doe',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e5ed18c926789c103997"),

FirstName: 'Jane',

LastName: 'Doe',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e60518c926789c103998"),

FirstName: 'John',

LastName: 'Smith',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e7fa18c926789c103999"),

FirstName: 'John',

LastName: 'Does',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e7fa18c926789c10399a"),

FirstName: 'Jane',

LastName: 'Doe',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

},

{

_id: ObjectId("62e3e7fa18c926789c10399b"),

FirstName: 'John',

LastName: 'Smith',

Age: 20,

Faculty: { Name: 'Engineering', Address: '123 St' },

Grades: [ { CourseName: 'Mongodb', Grade: 100, Pass: true } ],

isFired: false

}

]

```FacultySystemDB> db.student.find({isFired: {$eq: true}})```

  
  

```FacultySystemDB> db.student.find({$or: [{Age: {$gt: 21}, Faculty: {$ne: null}}]})```

  

```FacultySystemDB> db.student.find({FirstName: "Jane"}, {FirstName: 1, LastName: 1, isFired: 1})```

  

[

{

_id: ObjectId("62e3e5ed18c926789c103997"),

FirstName: 'Jane',

LastName: 'Doe',

isFired: false

},

{

_id: ObjectId("62e3e7fa18c926789c10399a"),

FirstName: 'Jane',

LastName: 'Doe',

isFired: false

}

]

  

#### Update the student with specific FirstName, and change his LastName.
##### •Try Update() statement.
##### •Try Update() with Mulit option.

```FacultySystemDB> db.student.update({name: "Jane"}, {$set: {name: "Julia"}})```

DeprecationWarning: Collection.update() is deprecated. Use updateOne, updateMany, or bulkWrite.

{

acknowledged: true,

insertedId: null,

matchedCount: 0,

modifiedCount: 0,

upsertedCount: 0

}

```FacultySystemDB> db.student.updateMany({FirstName: "John"}, {$set: {FirstName: "Jack"}})```

{

acknowledged: true,

insertedId: null,

matchedCount: 4,

modifiedCount: 4,

upsertedCount: 0

}

  

#### Delete Fired students.

```FacultySystemDB> db.student.deleteMany({isFired: true})```

{ acknowledged: true, deletedCount: 0 }

  

#### Delete all students collection.

```FacultySystemDB> db.student.drop()```

true

  

#### Delete the whole DB.

```FacultySystemDB> db.dropDatabase()```

{ ok: 1, dropped: 'FacultySystemDB' }

  

#### Create new database named: FacultySystemV2.
##### •Create student collection that has (FirstName, lastName, IsFired, FacultyID, array of objects, each object has CourseID, grade).
##### •Create Faculty collection that has (Faculty Name, Address).
##### •Create Course collection, which has (Course Name, Final Mark).
##### •Insert some data in previous collections.

```FacultySystemDB> use FacultySystemV2```

switched to db FacultySystemV2

  

```FacultySystemV2> db.createCollection("student")```

{ ok: 1 }

  

```FacultySystemV2> db.student.insert({FirstName: "John", LastName: "Doe", isFired: false, FacultyID: 111, Arr: [{CourseID: 555, Grade: 100}]})```

{

acknowledged: true,

insertedIds: { '0': ObjectId("62e3f96d18c926789c10399d") }

}

  

```FacultySystemV2> db.createCollection("faculty")```

{ ok: 1 }

  

```FacultySystemV2> db.faculty.insert({facultyName: "Science", Address: "123 St"})```

{

acknowledged: true,

insertedIds: { '0': ObjectId("62e3f9c618c926789c10399e") }

}

  

```FacultySystemV2> db.createCollection("Course")```

{ ok: 1 }

  

```FacultySystemV2> db.Course.insert({courseName: "mongodb", finalMark: 100})```

{

acknowledged: true,

insertedIds: { '0': ObjectId("62e3fa1518c926789c10399f") }

}
