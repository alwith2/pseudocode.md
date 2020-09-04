Start
//Begin Program
    Application receives order/payment/address
    Application sends to Restaurant
    Restaurant receives order
    Application sends addresses to robot
    Robot travels to Restaurant
    Robot notifies restaurant of its arrival using application
    Restaurant places order inside compartment of robot
    Robot travels to destination
    Robot notifies customer of its arrival
    Customer uses application to unlock compartment of robot
    Customer takes food from robot
//End Program

// Define objects
    Customer
        provides order, payment and address to application
    Application
        provides order, payment and address to restaurant
        provides addresses to robot
     Restaurant
        provides order to robot
    
INIT function
    create application
    create robot
    create customer
    create Restaurant
    create route

Robot INIT
   
Application
    INIT set up variables
        order received
        order sent to restaurant
            If(order.confirmed) send to robot
            Else(cancel.order)
            End If
    
Restaurant
    INIT set up variables
        order received
            If (order available) confirm.order
            Else cancel.order
            End If
        order prepared
        If order.ready, confirm.status

        order given to robot

Robot
    INIT set up variables
        order received
        If (available) confirm.order
            begin.route
        Else .queue
        If (arrives at restaurant) send.notification
        If (application.unlocks) unlock.compartment
        Else .wait
        If (food.received) begin.route
        Else .wait
        If (arrives) send.notification
        Else .proceed
        If (application.unlocks) unlock.compartment
        If (order.complete) .proceed
        If (.queue) proceed to restaurant
        Else proceed to charging hub

//END
