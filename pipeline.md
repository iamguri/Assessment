```
import groovy.sql.Sql

def sql = Sql.newInstance("jdbc:mysql://localhost:3306/testdb","guri", "abc", "com.mysql.jdbc.Driver")
pipeline {
    // Class.forName("com.mysql.jdbc.Driver")
    agent any 
    stages {
        stage('select') { 
            steps {
                sh ("select * from Contact")
                // query = "SELECT * from Contact"
                // println sql.rows(query)
                // sql.close()
            }
        }
        stage('Create database') { 
            steps {
                // 
                sh ("create")
            }
        }
        stage('Deploy') { 
            steps {
                // 
                sh ("select * from Contact")
            }
        }
    }
}

// stage ('SQL Test') {
//     node('remote_node') {
//         def sql = Sql.newInstance("jdbc:mysql://localhost:3306/testdb","guri", "abc", "com.mysql.jdbc.Driver")
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
