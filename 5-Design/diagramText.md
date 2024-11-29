@startuml

interface observer {
    + update(String emergencyMessage)
}

class subject {
    - List<Observer> observers
    + addObserver(Observer observer)
    + removeObserver(Observer observer)
    + notifyObserver(String name)
}

class user implements observer {
    - String name
    + User(String name)
    + update(String emergencyMessage)
}

class spots extends subject {
    - List<spotsList> spotsList
    + showListOfDangerSpots()
    + triggerEmergency(String message)
}

class auth {
    + login(String login,String password)
    + Wrong(String message)
}
class mainMenu {
    + showListOfNotifications(String listOfNotifications)
    + navigate(Window:Window)
}
class optionsSounds {
    + soundVolume(Int value)
    + signalName(String signalName)
    + returnToLastWindow(Window:Window)
}
class dangerSpots {
    + showListOfDangerSpots(String listOfDangerSpots)
    + showAmountOfDangerSpots(Int listOfDangerSpots.length)
    + returnToLastWindow(Window:Window)
}

class optionsSystem {
    + addNewSpot()
    + deleteSpot()
    + changeSpot()
    + returnToLastWindow(Window:Window)
}

class addNewSpot {
    - String path
    - String nameOfEquip
    - String nameInSystem
    - String description
    + addNewSpot(String path, String nameOfEquip, String nameInSystem, String description)
    + returnToLastWindow(Window:Window)
}

class deleteSpot {
    + showListOfDangerSpots(String listOfDangerSpots)
    + deleteSpotInSystem(String nameInSystem)
    + returnToLastWindow(Window:Window)
}

class changeSpot {
    + changeSpot(String nameInSystem)
    + returnToLastWindow(Window:Window)
}

subject o-- observer : "Сповіщає"
auth --> mainMenu : "логін"

mainMenu --> optionsSounds 
mainMenu <-- optionsSounds 

mainMenu --> dangerSpots
mainMenu <-- dangerSpots

mainMenu --> optionsSystem
mainMenu <-- optionsSystem

optionsSystem --> addNewSpot
optionsSystem <-- addNewSpot

optionsSystem --> deleteSpot
optionsSystem <-- deleteSpot

optionsSystem --> changeSpot
optionsSystem <-- changeSpot

addNewSpot --> spots
deleteSpot --> spots
changeSpot --> spots

@enduml
