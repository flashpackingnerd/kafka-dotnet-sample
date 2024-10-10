# Kafka .NET Core Producer and Consumer 

## Introduction
This sample app contains a .NET Core application that produces sample data on to a Kafka topic and the also consumes the topic data. The [Kafka](https://kafka.apache.org/) broker, [Zookeeper](https://zookeeper.apache.org/) & [control center](https://docs.confluent.io/current/control-center/index.html) is docker images that gets pulled in the docker-compose file.

## Prerequisites
* [.NET 8](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
* [Docker](https://www.docker.com/products/docker-desktop/)

## Getting started
To get you the application running just execute the following in cmd/bash:
```
docker-compose up
```

## Running App in Docker
This can be used if you have your own Kafka environment already setup:

```
docker build --pull -t kafka-app .
```
```
docker run -it --rm -p 5000:80 --name kafka-app kafka-app
```

## UI
 - [Control Center UI](http://localhost:9021/)

___
## Future Changes
I have commented out the SSL authentication for the producer and the consumer because I need to set up the SSL on the broker.
### Creating SSL certificates for Kafka
1. Generate a key file that you will use to generate a certificate signing request.
2. Create a certificate signing request to send to a certificate authority.
3. Download a pem file from certificate authority in OpenSSL format, rename it to secure.pem
4. Open .pem file in a text editor of your choice and remove all the Subject information from the file so that you have this left:
```
-----BEGIN CERTIFICATE-----
[ENCODED INFORMATION OMITTED]
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
[ENCODED INFORMATION OMITTED]
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
[ENCODED INFORMATION OMITTED]
-----END CERTIFICATE-----
```

5. Open the .key file and copy its contents and paste it at the bottom of your .pem file so that it finally looks like this:
```
[ENCODED INFORMATION OMITTED]
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
[ENCODED INFORMATION OMITTED]
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
[ENCODED INFORMATION OMITTED]
-----END CERTIFICATE-----
-----BEGIN PRIVATE KEY-----
[ENCODED INFORMATION OMITTED]
-----END PRIVATE KEY-----
```
