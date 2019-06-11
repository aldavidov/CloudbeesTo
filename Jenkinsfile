pipeline {
    agent any

    stages {
        stage ('Deploy PHP & Apache') {
            steps {
                sh 'docker 2>/dev/null 1>&2 rm -f global_dev || true'
                sh '''
                    docker run --name global_dev -d --restart always \
                    -p 80:80 -v /app/img:/var/www/html/img \
                    php:7.2.1-apache
                '''
                sh 'docker exec global_dev docker-php-ext-install pdo pdo_mysql'
                sh 'docker restart global_dev'
            }
        }
        stage ('Create db.config') {
            steps {
                withCredentials([conjurSecretCredential(credentialsId: 'mysql_address', variable: 'MYSQL_ADDRESS'),
                    conjurSecretCredential(credentialsId: 'mysql_username', variable: 'MYSQL_USERNAME'),
                    conjurSecretCredential(credentialsId: 'mysql_password', variable: 'MYSQL_PASSWORD')]) {
                        sh 'echo -n "${MYSQL_ADDRESS},${MYSQL_USERNAME},${MYSQL_PASSWORD}" > db.config'
                }            
            }
        }
        stage ('Create index.php') {
            steps {
                sh '''
                    cat << 'EOF' > global_dev.php
                    <?php
                        $contents = file_get_contents('db.config');
                        $db = explode(',', $contents);
                        $connection = new PDO("mysql:host=$db[0];dbname=butlers_pets", $db[1], $db[2]);
                        $statement = $connection->query('SELECT pet_file_path FROM global');
                        $pet = $statement->fetch();
                    ?>
                    <html>
                        <head>
                            <title>Butler's Pets - CloudBees Days 2019</title>
                        </head>
                        <body>
                            <div align="center">
                                <h1>Butler's Pet Authorized to Global</h1><br />
                                <img src="<?php echo $pet[0] ?>" />
                            </div>
                        </body>
                    </html>
                '''
            }
        }
        stage ('Copy index.php & db.config') {
            steps {
                sh 'docker cp global_dev.php global_dev:/var/www/html/index.php'
                sh 'docker cp db.config global_dev:/var/www/html/db.config'
            }
        }
    }

    post {
        always {
            sh 'rm -f global_dev.php db.config'
        }
        success {
            echo 'http://pets.cloudbeesdays.demo/index.php'
        }
        failure {
            sh 'docker rm -f global_dev'
        }
    }
}
training@training-vm:~/Conjur$ 
training@training-vm:~/Conjur$ 
training@training-vm:~/Conjur$ 
training@training-vm:~/Conjur$ 
training@training-vm:~/Conjur$ 
training@training-vm:~/Conjur$ 
training@training-vm:~/Conjur$ cat /home/training/Conjur/jenkinsfiles/global/Jenkinsfile
pipeline {
    agent any

    stages {
        stage ('Deploy PHP & Apache') {
            steps {
                sh 'docker 2>/dev/null 1>&2 rm -f global_dev || true'
                sh '''
                    docker run --name global_dev -d --restart always \
                    -p 80:80 -v /app/img:/var/www/html/img \
                    php:7.2.1-apache
                '''
                sh 'docker exec global_dev docker-php-ext-install pdo pdo_mysql'
                sh 'docker restart global_dev'
            }
        }
        stage ('Create db.config') {
            steps {
                withCredentials([conjurSecretCredential(credentialsId: 'mysql_address', variable: 'MYSQL_ADDRESS'),
                    conjurSecretCredential(credentialsId: 'mysql_username', variable: 'MYSQL_USERNAME'),
                    conjurSecretCredential(credentialsId: 'mysql_password', variable: 'MYSQL_PASSWORD')]) {
                        sh 'echo -n "${MYSQL_ADDRESS},${MYSQL_USERNAME},${MYSQL_PASSWORD}" > db.config'
                }            
            }
        }
        stage ('Create index.php') {
            steps {
                sh '''
                    cat << 'EOF' > global_dev.php
                    <?php
                        $contents = file_get_contents('db.config');
                        $db = explode(',', $contents);
                        $connection = new PDO("mysql:host=$db[0];dbname=butlers_pets", $db[1], $db[2]);
                        $statement = $connection->query('SELECT pet_file_path FROM global');
                        $pet = $statement->fetch();
                    ?>
                    <html>
                        <head>
                            <title>Butler's Pets - CloudBees Days 2019</title>
                        </head>
                        <body>
                            <div align="center">
                                <h1>Butler's Pet Authorized to Global</h1><br />
                                <img src="<?php echo $pet[0] ?>" />
                            </div>
                        </body>
                    </html>
                '''
            }
        }
        stage ('Copy index.php & db.config') {
            steps {
                sh 'docker cp global_dev.php global_dev:/var/www/html/index.php'
                sh 'docker cp db.config global_dev:/var/www/html/db.config'
            }
        }
    }

    post {
        always {
            sh 'rm -f global_dev.php db.config'
        }
        success {
            echo 'http://pets.cloudbeesdays.demo/index.php'
        }
        failure {
            sh 'docker rm -f global_dev'
        }
    }
}
