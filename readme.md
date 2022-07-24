##### keytool is a key and certificate management utility. It allows users to administer their own public/private key pairs and associated certificates for use in self-authentication (where the user authenticates himself/herself to other users/services) or data integrity and authentication services, using digital signatures.

##Open Windows Command Prompt

 ###Type following commands

     keytool -genkeypair -alias local_ssl -keyalg RSA -keysize 2048 -storetype PKCS12 -keystore local-ssl.p12 -validity 365 -ext san=dns:localhost
####System will ask you to provide some information and ask you to set a password

####After successfully generated again type following commands
       
    keytool -export -keystore local-ssl.p12 -alias local_ssl -file local-cert.crt

After successfully executing you will see a local-cert.crt in same directory 

### Install the certificate file by clicking on the file name


In a Grails app update you application.yml as following
    
     development:
        server:
            port: 8080
            ssl:
                keyStore: C:\cert\ssl\self-signed\local-ssl.p12 // change as your directory
                keyStorePassword: localhost // which you entered while generating
                keyAlias: local_ssl // change if you was changed
 