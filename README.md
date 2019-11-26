# OOAE-Notes

Observer

- Defines a one to many dependency between objects, so that when object changes state, all its
dependencies are notified and updated automatically.


<<interface>>                       <<interface>>
   Subject				Observer
------------------                  ---------------
+attach(Observer o) ----------->     +update()
+detach(Obeserver o) 
+Notify()				^
					|	
					|	
					|
				      
ConcreteSubject			     ConcreteObserver
-------------                        ----------------
-subjectState                        -observerState
-------------                        ----------------
+attach(Observer o)  <-----------    +update()   
+detach(Observer o)		     
+notify()
+getState()
+setState()


- ConcreteSubject has a reference of ConcreteObserver.
- Once the notified method in the ConcreteSubject has been updated, the update method in 
ConcreteObserver automatically gets updated.


Consequences

- Losing coupling between Subject and Observer
- Subject only knows about its observers is that the observer implements Observer interface. You can
register or delete any observer without affecting the subject.

- Support for broadcast communication
- Notification about the subject state change does not need to specify its receiver. This notification
is broadcasted to all interested objects that subscribed to it.

- Debugging is difficult.

- Unexpected updates.
(Due to the broadcast communication)

