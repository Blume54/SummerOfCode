# Week 5: Server Side :vhs:

## Day 1: Read your Heroes :calling:
We can already edit our heroes, but any changes are immediately lost in the void.
 - [Enable HTTP services](https://angular.io/tutorial/toh-pt6#enable-http-services)
   - Follow the instructions
   - Perform the changes you did for app.module.ts on app.module.tns.ts as well
 - [Simulate a data server](https://angular.io/tutorial/toh-pt6#simulate-a-data-server)
   - Follow the instructions
   - Use the names of your heroes
   - Perform the changes you did for app.module.ts on app.module.tns.ts as well
 - [Heroes and HTTP](https://angular.io/tutorial/toh-pt6#heroes-and-http)
   - Follow the instructions
   - Tomorrow we will continue with Update heroes

## Day 2: Create, Update and Delete your Heroes :cupid:
Starting today you can add your new heroes and dispose of old, weak ones.
 - Update heroes https://angular.io/tutorial/toh-pt6#update-heroes
   - Follow the instructions
   - Clarification regarding hero-detail.component.html
     - Add the button before the final \</div>
   - At the end of hero-detail.component.tns.html, before \</StackLayout> add
     ```
     <Button text="Save" (tap)="save()"></Button>
     ```
 - Add a new hero https://angular.io/tutorial/toh-pt6#add-a-new-hero
 - Delete a hero https://angular.io/tutorial/toh-pt6#delete-a-hero
 - Run both your web and mobile apps
 
