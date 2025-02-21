This is a repository containing a Java Spring Boot application for exposing some HTTP APIs to work with an appointment management system via Dialogflow. It uses a in-memory database.

# DialogFlow Front-end

## Intents

Intents and Webhooks for this appointment service:

* Sign in a user on the system 
   * Intent name: SignIn
   * Input parameters: 
     * identityDocumentNumber (@sys.any)
     * givenName (@sys.person)
   * Postconditions:
     * The user is now identified
  

* Get the next appointment of the user
  * Intent name: NextAppointment
  * Preconditions:
     * The user must be properly identified


* Make a new appointment
  * Intent name: MakeAppointment
  * Input parameters: 
    * appointmentType (@AppointmentType)
  * Preconditions:
     * The user must be properly identified
  * Postconditions:
     * An appointment is pending to confirm
 
* Confirm the current appointment 
  * Intent name: MakeAppointment-confirm
  * Preconditions:
     * The user must be properly identified
     * An appointment is pending to confirm
  * Postconditions:
    * The appointment is now confirmed

* Cancel the current appointment 
  * Intent name: MakeAppointment-cancel 
  * Preconditions:
    * The user must be properly identified
    * An appointment is pending to confirm
  * Postconditions:
    * The appointment is cancelled
  
## Entities
List of entities for this appointment service:
* AppointmentType
  * CUT: corte, pelar, recortar
  * COLORING: colorear, teñir, pintar
  * CONSULTATION: consultar, dudas, aconsejar

## Fulfillment
Configure dialogflow webhook URL to: https://RANDOMNUMBERS.ngrok-free.app/dialogflow
Please, revise that your intent names and param names match with the expected ones. They are provided below:


# Java Back-end

## SETUP

1. Install Java (version 11 is required)
2. Download asset: *citasapi-x-y.z.jar* from [Github Releases](https://github.com/ruizrube/citasAPI/releases) 
3. Run: $ **java -jar citasapi-x-y.z.jar** from the command line
4. Check that [http://localhost:8080/users](http://localhost:8080/users) provides some demo users in JSON format. See other HTTP APIs below.
5. Install the [ngrok](http://ngrok.com)	tool and configure it with the provided key
6. Run ngrok from the command line: $ **ngrok http 8080** (please aware of the number port)
7. Copy the forwarding URL **https://RANDOMNUMBERS.ngrok-free.app** -> http://localhost:8080 
8. Check https://RANDOMNUMBERS.ngrok-free.app/users provides some demo users in JSON format

## REST API

HTTP APIs for this appointment service 
* List of users
  * URI: https://localhost:8080/users
* List of appointments
  * URI: https://localhost:8080/appointments
* DialogFlow Webhooks
  * URI: https://localhost:8080/dialogflow


