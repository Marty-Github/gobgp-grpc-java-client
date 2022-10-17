A try to implement [gobgp grpc java client](https://github.com/Marty-Github/gobgp-grpc-java-client) by means of gradle build tool.  
Projects [grpc-java](https://github.com/grpc/grpc-java) and [protobuf-gradle-plugin](https://github.com/google/protobuf-gradle-plugin)
are used as dependencies and plugin. It's building and running with error:

```
io.grpc.StatusRuntimeException: UNIMPLEMENTED: unknown service apipb.GobgpApi
at io.grpc.stub.ClientCalls.toStatusRuntimeException(ClientCalls.java:271)
at io.grpc.stub.ClientCalls.getUnchecked(ClientCalls.java:252)
at io.grpc.stub.ClientCalls.blockingUnaryCall(ClientCalls.java:165)
at apipb.GobgpApiGrpc$GobgpApiBlockingStub.getBgp(GobgpApiGrpc.java:3033)
at grpc.Client.build_path(Client.java:80)
at grpc.Client.process(Client.java:123)
at grpc.Client.main(Client.java:136)
```

It can be run from project's dir by command:  
```gobgp-grpc-java-client$> ./gradlew run```  

The **_*.proto_** files are taken from [gobgp/api](https://github.com/osrg/gobgp/tree/master/api) .

The only example [gobgp-grpc-java](https://github.com/ng-labo/gobgp-grpc-java) I've found uses Maven tool and can't be built.
I use java client's source code from that example in my project.

My environment:
OS: Windows 10 => WSL2 => Ubuntu 20.04
JDK: java-11-openjdk (linux)

```$>java -version```  
_openjdk version "11.0.16" 2022-07-19
OpenJDK Runtime Environment (build 11.0.16+8-post-Ubuntu-0ubuntu120.04)
OpenJDK 64-Bit Server VM (build 11.0.16+8-post-Ubuntu-0ubuntu120.04, mixed mode, sharing)_

GoBgp service is installed under WSL2(Ubuntu 20.04) by command:  
```$>sudo apt-get -y install gobgpd```

GoBgp's version:  
```$>apt-cache policy gobgpd```  
_gobgpd:  
  Installed: 2.12.0-1  
  Candidate: 2.12.0-1  
  Version table:  
 *** 2.12.0-1 500  
    500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages  100 /var/lib/dpkg/status_  

GoBgp service is runnig with configuration file taken from your [Getting Started](https://github.com/osrg/gobgp/blob/master/docs/sources/getting-started.md).  
GoBgp CLI is working well. All commands are executed.  


It's necessary to clarify what's wrong with it.

Is there any working example of grpc java client for gobgp?
