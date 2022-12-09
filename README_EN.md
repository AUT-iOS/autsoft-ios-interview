# South-Zubony International Airport (*SZIA*) application

![](img/logo.png)

## Tasks needs to be done
  - Create modell classes: `Airline`, `News`, `Flight`, `Complaint`
  - Create the base of the application with a `UITabBarController` with 5 view-controller
  - Create arrive and depart flights screen (including save favourites)

## Introduction
Many people have already mentioned how good it would be if South-Zubony airport also had a mobile application, since millions of people travel through Zubony every day and the airport's website is far from perfect. Fortunately, there is a fairly serious *web API* available for flight information, and Zubonyi passengers typically use an iPhone.

In the next 8 hours you have to make this application for `iOS` platform. The minimum iOS version is `iOS 13` with `Swift 5.7`.


## Specification
The application contains 4 main functionality:

  - show and save flight information
  - show airport news 
  - show the airport on the map
  - complaints.

### Flight information
In the application, it is possible to view a list of departing and arriving flights. It is possible to mark individual flights as favorites, in which case it must be able to be saved in the phone's local database and displayed even without the Internet. Flight information must be downloaded from the Internet.

### News
The airport's current news should be displayed in a list: clicking on an item will display a detailed description of the news. The news must be downloaded from the Internet.

### Map
The coordinates of Zubony are the same as the coordinates of the BUTE Q building (47.4733222,19.0576915,17), the airport must be displayed on a map view.

### Complaints
It is possible to make a complaint, which means filling out and sending a form, for which it is also possible to attach a picture.

## Model
The application contains the following objects, between the bracket you can see the related data:

  - `Flight company` (*image*, *name*, *id*)
  - `Flight` (*flight number*, *id*, *departure*, *arrive*, *start city*, *destination city*, *status*, *checkin number*, *gate number*, *delay*, *comment*, *flight company id*)
  - `News` (*id*, *address*, *content*, *date*)
  - `Complaint` (*content*, *subject of complaint*, *complainant name*, *complainant email address*, *complainant complainant phone number*, *image*)

## Server

The backend of the application can be reached at [`https://szia-backend.autsoft.hu/api/`](https://szia-backend.autsoft.hu/api/). You can try out the request at [`https://szia-backend.autsoft.hu/explorer/`](https://szia-backend.autsoft.hu/explorer/). You need to use the following endpoints:

- `GET` /Airlines
- `POST` /Complaints
- `GET` /Flights
- `GET` /News

## Application screens
Different functions of the application are displayed on different screens, which are located on separate pages (tabs). The screens included here are sketches(!), part of the task is that everyone can design the application based on their own taste based on the sketches.

### Arriving flights
On the first page there is a screen for arriving flights. Here you can see a list of arriving flights. The list can be updated by pressing the update button (or e.g. *swipe to refresh*), in which case the latest flight information will be downloaded from the server (optionally by *swiping* down the list). By clicking on an element, it can be marked as a favorite, which must be able to be stored in a database. This must be indicated in some way, e.g. a star or inscription.

![](img/flight_list.png)


### Departing flights
Same as arriving screen.

### News and news details
The third tab contains the news view, which displays the latest news in chronological order. Click on a news item to see its details.

### Map screen
In the map view, South Zubony is visible on the map, and by clicking on it, basic information about the airport appears.

### Complaint
On the last page you can see the complaint report, which is a *form* to be filled out. After it has been executed, it can be sent to the server by clicking the ``Send'' button. It is also possible to upload a picture to the server.
