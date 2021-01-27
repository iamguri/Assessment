```
import groovy.sql.Sql

def sql = Sql.newInstance("jdbc:mysql://localhost:3306/testdb","root", "abc", "com.mysql.jdbc.Driver")
pipeline {
    // Class.forName("com.mysql.jdbc.Driver")
    agent any 
    stages {
        stage('insert') { 
            steps {
                sh ("insert into Contact (Firstname, Lastname, Phone, Mobile, email) values("gurjeet", "singh","123456789", "123456", "gurjeetbhari@gmail.com") ")
                // query = "insert into Contact (Firstname, Lastname, Phone, Mobile, email) values("gurjeet", "singh","123456789", "123456", "gurjeetbhari@gmail.com")"
                // println sql.rows(query)
                // sql.close()
            }
        }
        stage('Add new user') { 
            steps {
                // 
                sh ("create user 'guri'@'localhost' identified by 'abc' ")
                sh ("GRANT ALL PRIVILEGES ON database_name.* TO 'guri'@'localhost' ")
                sh ("flush privileges")
            }
        }
        stage('Alter Table') { 
            steps {
                // 
                sh ("alter table Contact add address varchar(255) ")
            }
        }
    }
}

// stage ('SQL Test') {
//     node('remote_node') {
//         def sql = Sql.newInstance("jdbc:mysql://localhost:3306/testdb","root", "abc", "com.mysql.jdbc.Driver")
//         query = "SELECT * from Contact"
//         println sql.rows(query)
//         sql.close()
//     }
// }
// pipeline {
//     agent any 
//     // stages {
//         stage('SQL') { 
//             steps {
//                 def sql = Sql.newInstance("jdbc:mysql://localhost:3306/testdb","guri", "abc", "com.mysql.jdbc.Driver")
//                 query = "SELECT * from Contact"
//                 println sql.rows(query)
//                 sql.close()
//             }
//         }
//     // }
// }
```
