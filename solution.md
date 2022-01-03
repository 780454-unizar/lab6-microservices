# Solution
## The two services are running and registered
First of all, we have to run the registration service. Then, we can run the other services. We can run every one using the following commands: 
```
./gradlew :registration:bootRun
./gradlew :accounts:bootRun
./gradlew :web:bootRun
```

Once both services are running, they register into the Eureka service. 

Registration
!.[Registration].(images/registration.png)

Accounts 
!.[Accounts].(images/accounts.png)

Web 
!.[Web].(images/web.png)

## The service registration has the two services registered
Once the services are running and registered, you can access to Eureka in order to check their status: 

!.[Eureka1].(images/2Servicios.png)

## A second account service is running in the port 4444 and it is registered
There is a file called `application.yml` where we can set the ports of the service. We only have to change `port:2222` to `port:4444`. We can find this file in `accounts/src/main/resources`. 

Accounts port:4444
!.[Accounts4444].(images/accounts4444.png)

Once the port is changed, we run the service and we can check its status in the same way as we did in the previous case: 

!.[Eureka2].(images/3Servicios.png) 

## What happens when you kill the service with port 2222? Can the web service provide information about the accounts? Why? 

If we kill the service which is running in `port:2222`, it dissapears from the registration service. It dissapears from Eureka Dashboard too. 

!.[Eureka3].(images/2222Muerto.png)

During a short period of time, the web service returns an Internal Server Error and Eureka redirects us to the dead service.

!.[Error].(images/Error.png)

Once Eureka detects that the service is dead, it returns the user information without problems. This happens because Eureka is a mediator between the accounts service and the web services. 

!.[Detalles].(images/Detalles.png)

