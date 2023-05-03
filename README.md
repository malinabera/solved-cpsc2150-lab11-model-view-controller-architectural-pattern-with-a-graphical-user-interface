Download Link: https://assignmentchef.com/product/solved-cpsc2150-lab11-model-view-controller-architectural-pattern-with-a-graphical-user-interface
<br>
In this lab you will be working with the Model-View-Controller architectural pattern with a Graphical User Interface created using Java Swing. The <strong>View</strong> (GUI) is provided for you, and you have already completed the <strong>Model</strong>. For this lab, you will just need to complete the <strong>Controller</strong>.




<h1>Instructions</h1>

You will need to create a new project with a package called cpsc2150.banking. Add your Mortgage and Customer classes and interfaces from lab 6 to that package. (<strong>Note:</strong> You will need to create the models folder for these files to match their package structure.) Add the IMortgageView and IMortgageController interfaces from last week’s lab to the package and the provided MortgageGUIView class to the package as well to be your Graphical User Interface.




<h2>MortgageGUIApp.java</h2>

MortgageGUIApp will be a very simple class. It will contain our main method that will be the entry point of the program. All it will do is declare an instance of IMortgageView and IMortgageController, and connect them. After that the system will wait for an event from the IMortgageView object. The code should look like:




package cpsc2150.banking;




public class MortgageGUIApp {

public static void main(String[] args) {         IMortgageView view = new MortgageGUIView();

IMortgageController controller = new MortgageGUIController(view);         view.setController(controller);

}

}




This type of set up is common when using MVC architectural pattern in Java. We just need the entry point to set up our <strong>Controller</strong> and <strong>View</strong>. Set up your configuration so this is the entry point for your program.




<h2>IMortgageView.java and MortgageGUIView.java</h2>

This interface and implementation will serve as the <strong>View</strong> layer of our system. They provide several methods to get input from the user and display output to the screen. The <strong>View</strong> layer does not provide any input validation. That will need to be handled by the <strong>Controller</strong>.

Inspect the interface to make sure you understand what methods are available to you. Read through the code for the view as an example of building an interface in Java Swing. <strong>You should not need to make any changes to these files. </strong>

<strong> </strong>

<strong>Note:</strong> The IMortgageView and MortgageGUIView files should be placed inside a new views folder to match the package cpsc2150.banking.views.




<h2>MortgageGUIController.java</h2>

The MortgageGUIController class implements IMortgageController and serves as the <strong>Controller</strong> layer in our MVC architecture. It controls the flow of control in our program. This class is able to use both the view and the model layers to accomplish this task. This class will check to make sure the data that the user provides (through the <strong>View</strong> layer) meets the preconditions that exist in our <strong>Model</strong> layer. If the input is not valid, the <strong>Controller</strong> will (through the <strong>View</strong>) alert the user to the error and wait for them to correct their input and resubmit. If there are multiple errors the <strong>Controller</strong> only needs to report one to the user. The MortgageGUIController class will also use the <strong>Model</strong> layer (Mortgage and Customer class) to apply for the mortgage. After a mortgage has been applied for, the <strong>Controller</strong> will (through the <strong>View</strong> layer) say whether the loan was approved or not. If the loan was approved, then the rate and monthly payments will be displayed as well. If the loan was denied then 0 will be displayed for the rate and monthly payment.

The MortgageGUIController class will have one private field, an IMortgageView object, which is set by an argument passed into the constructor. The MortgageGUIController class will have one public method, called submitApplication() which is called after the user hits the submit button. The view layer is already observing the submit button, and will call submitApplication when the user clicks the submit button. Remember, in last week’s lab we were following procedure-driven control and now we will be following event-driven control. submitApplication() will just be responding to one click of the button, not running several applications.

All the logic concerning validating the <strong>Model</strong>’s preconditions, and the order of events, is handled by the <strong>Controller</strong> layer. The logic concerning the mortgage application or the customer itself are handled by the <strong>Model</strong> Layer.

Your starter code for the <strong>Controller</strong> layer is as follows:




package cpsc2150.banking.controllers;




public class MortgageGUIController implements ImortgageController {     private IMortgageView view;




public MortgageGUIController(IMortgageView v) {         view = v;

}

public void submitApplication() {

//Your code here

}

}

<strong>Note:</strong> The IMortgageController and MortgageGUIController files should be placed inside a new controllers folder to match the package cpsc2150.banking.controllers.




<h1>TIPS and additional Requirements</h1>

<ul>

 <li>You do not need to provide a makefile for this assignment, nor do you need to test your code on SoC Unix (GUIS and Unix don’t play well).</li>

 <li>You will zip up your IntelliJ project directory and submit that on handin.</li>

 <li>You do not need to provide any automated testing, although you should test your program.</li>

 <li>You do not need to provide any contracts for your code as they should be available from other assignments.</li>

 <li>You <strong>DO</strong> need to comment your code</li>

 <li>You need to follow the Model-View-Controller architectural pattern for this assignment.

  <ul>

   <li>All interaction with the user goes through the <strong>View</strong> <strong>View</strong> does not have access to the <strong>Model</strong>.</li>

   <li><strong>Controller</strong> handles input validation, and the order of events of the program. The <strong>Controller</strong> has access to the <strong>View</strong> and the <strong>Model</strong>, so it is the go between for those two layers</li>

   <li>The <strong>Model</strong> handles our entity objects and the “lower level” logic. It does not have any access to the other two layers.</li>

  </ul></li>

 <li><strong>Follow our best practices:</strong> No magic Numbers, information hiding, separation of concerns, etc.</li>

 <li>The <strong>Controller</strong> will be very different from lab 10, as the flow of control is very different now that we are using a GUI and are reacting to button clicks.</li>

 <li>Make sure to understand what all the methods in our <strong>View</strong> layer do. They will be very helpful.</li>

 <li>Depending on the resolution of your screen, it may be difficult to read the text on the GUI. Java Swing is not great with font sizes.</li>

 <li>You may not need all the methods provided by the IMortgageView interface to complete this assignment. It is fine to not call all of the methods provided.</li>

</ul>


