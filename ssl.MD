# Self signed certificates

### Install mkcert using npm

    npm install -g mkcert

### Genarate Cert for react like application


     mkcert create-ca

    mkcert create-cert



### install certifacte into System


    double click on ca.crt
    install certificate-->local machine->place all_cert to following place->select trusted Root certtifate authorities-->finish


- set HTTPS=true&&set SSL_CRT_FILE=./cert/cert.crt&&set SSL_KEY_FILE=./cert/cert.key&&


    or overiide ->cert.key & cert.crt  in ->noude-Moudules->webpack-development-server->ssl->server.pem



# Spring boot apps 


- use react pem file  and conevrt to p12 format and place in java resouce folde


     openssl pkcs12 -export -in server.pem -out client.p12


### other way

- genarate jks using java key tools

     keytool -genkey -alias spring-https -storetype JKS -keyalg RSA -keysize 2048 -validity 365 -keystore rtls.jks
 
    and genarte  cacert file and place into java/bin/lib/secutiy folder


- put  rtls.jks into resource folder

    application.yaml changes 


	server:
	  ssl:
	    key-alias: spring-https
	    key-store: classpath:rtls.jks
	    key-store-type: JKS
	    key-password: password
	    
	  port: 7777  