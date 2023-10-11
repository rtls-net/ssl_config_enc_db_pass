# Use Encrypted Password in application.yaml

- You can use Jasypt to encrypt properties, so you could have your property like this:

     db.password=ENC(XcBjfjDDjxeyFBoaEPhG14wEzc6Ja+Xx+hNPrJyQT88=)

    Jasypt allows you to encrypt your properties using different algorithms, once you get the encrypted property you put inside the ENC(...). For instance, you can encrypt this way through Jasypt using the terminal:

- Genarate Encypted password

    encrypted-pwd$ java -cp %homedrive%%homepath%/.m2/repository/org/jasypt/jasypt/1.9.3/jasypt-1.9.3.jar  org.jasypt.intf.cli.JasyptPBEStringEncryptionCLI input="tryagaIN" password=encDB algorithm=PBEWithMD5AndDES


-Output

----ENVIRONMENT-----------------

Runtime: Oracle Corporation Java HotSpot(TM) 64-Bit Server VM 24.45-b08



----ARGUMENTS-------------------

algorithm: PBEWithMD5AndDES
input: contactspassword
password: supersecretz



----OUTPUT----------------------

XcBjfjDDjxeyFBoaEPhG14wEzc6Ja+Xx+hNPrJyQT88=
To easily configure it with Spring Boot you can use its starter jasypt-spring-boot-starter with group ID com.github.ulisesbocchio

Keep in mind, that you will need to start your application using the same password you used to encrypt the properties. So, you can start your app this way:

mvn -Djasypt.encryptor.password=supersecretz spring-boot:run
Or using the environment variable (thanks to spring boot relaxed binding):

export JASYPT_ENCRYPTOR_PASSWORD=supersecretz
mvn spring-boot:run


----reset mysql pass
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('password');
FLUSH PRIVILEGES;