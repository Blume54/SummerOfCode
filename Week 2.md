# Week 2: Start Coding :vibration_mode:

If you can't remember how to do something we already did, look it up in [last week's curriculum](https://github.com/phaze9/SummerOfCode/blob/master/Week%201.md)!

## Day 1: Git and Test :hotsprings:
Work with Git(Hub) and fix the tests.
 - Open the Projects/heroes folder in Visual Studio Code
   - Open the Source Control tab
   - Note that many new files are listed
   - These were created by the "ng build" command we ran yesterday
 - Edit the file .gitignore
   - Add a new line at the end
     ```
     /dist
     ```
   - And save the file using Cmd/Ctrl-S
   - Now you should only have one outgoing change, the file .gitignore
 - Click Synchronize Changes :doughnut: in the blue bar on the bottom left of Visual Studio
   - Open your heroes repository on the GitHub website
   - Notice how all your changes from yesterday  are visible there
 - Go back to the Source Control tab in Visual Studio
   - Enter a commit message: Updated .gitignore
   - Add the file .gitignore :heavy_plus_sign:
   - And commit  
 - Yesterday you might have noticed that some tests we ran in the Terminal failed
   - We broke these when we changed the application two days ago
   - Let's fix them!
 - Open a Terminal and change to the ~/Projects/heroes folder
   - Then run
     ```
     ng test
     ```
   - One test succeeded, two failed
 - AppComponent > should have as title 'heroes'
   - Open the file app.component.spec.ts in Visual Studio
   - Change line 22 until the test succeeds
     - The test is rerun automatically when you save the file
   - Look at the [changes we did at the end of day 6](https://angular.io/tutorial/toh-pt0#change-the-application-title) to get an idea what you need to fix 
 - AppComponent > should render title
   - Change line 29 in the same file to
     ```
     expect(compiled.querySelector('h1').textContent).toContain('Tour of Heroes');  
     ```
 - Don't forget to commit and synchronize your changes
   - Use the message: Fixed the tests
 
## Day 2: Run the App :running:
Run your heroes app manually and automatically.
 - Open a Terminal and change to the ~/Projects/heroes folder
 - Run the heroes app using
   ```
   ng serve --open
   ```
   - This will start a server hosting your app and open a browser to http://localhost:4200
 - Now open the heroes folder in Visual Studio Code
 - Change the color of the title to your favorite color
   - Edit the file src/styles.scss
   - Change the color of the 'h1' element to one of the following
     ![CSS Color Names](https://miro.medium.com/max/1400/1*IUKKnAi_7ZjM91Fouh2yxA.png)
 - Commit and synchronize your change 
   - Briefly describe what you did in the commit message
 - We can also run our app automatically to test it
   - Stop the app by pressing Ctrl-C in the Terminal window
   - Yesterday we ran the unit tests
   - Today we will run the e2e (end-to-end) tests
     ```
     ng e2e
     ```
 - As with the unit tests we also broke an e2e test with our changes three days ago
   ```
   1) workspace-project App should display welcome message
   - Failed: No element found using locator: By(css selector, app-root .content span)
   ```
 - Fix the failing test
   - In app.po.ts we need to change where the title is read from in line 9
     - Replace
       ```
       by.css('app-root .content span')
       ```
     - With
       ```
       by.css('h1')
       ```
   - Find out what to change in e2e/src/app.e2e-spec.ts
     - Hint: The fix is similar to what we did yesterday
   - Rerun the e2e tests to verify  
   - Again: Commit and synchronize your change
 - Head over to your heroes repository on GitHub
   - Invite your tutor as a collaborator so they can review your work

## Day 3: Show your Hero :smiling_imp:
Let's finally write some code!
 - First install a few more useful Visual Studio extensions
   - From the Extensions tab in Code
   - Angular Language Service
   - Markdown All in One
   - ESLint
 - Create the heroes component
   - Use the Angular CLI from your heroes Project in a Terminal
     ```
     ng generate component heroes  
     ```
   - [Read about what you just did](https://angular.io/tutorial/toh-pt1#create-the-heroes-component)
 - Don't forget to save your changes in Visual Studio along the way
 - [Add a hero property](https://angular.io/tutorial/toh-pt1#add-a-hero-property)
   - We add this on a new line before 'constructor() { }'
   - Followed by an empty line
 - Run the heroes app in a Terminal
   - Like we did yesterday
 - [Show the HeroesComponent view](https://angular.io/tutorial/toh-pt1#show-the-heroescomponent-view)
   - This will display the new heroes component in your app
   - Enough for today, tomorrow we will turn it into a real hero
 - Commit and synchronize your changes

## Day 4: Identify your Hero :bust_in_silhouette:
This is your hero.
 - Run your heroes app in a Terminal and continue coding in Visual Studio  
 - Give your hero a proper name
   - Edit heroes/src/app/heroes/heroes.component.ts
 - [Create a Hero interface](https://angular.io/tutorial/toh-pt1#create-a-hero-interface)
   - Create a new hero.ts file in the src/app folder
   - While applying the changes to heroes.component.ts look at each change
     -  And try to understand what it does
   - When you are done, make sure your Terminal window displays "Compiled successfully."
 - [Show the hero object](https://angular.io/tutorial/toh-pt1#show-the-hero-object)
   - Replace the content of heroes.component.html
 - Commit and synchronize your changes
 
## Day 5: Test your Hero :question:
Is your hero there?
 - Add a unit test: Check your hero's name
   - Open src/app/heroes/heroes.component.spec.ts in Visual Studio
   - Add a new test below the existing test 'should create'
     ```
     it('should be called Windstorm', () => {
       expect(component.hero.name).toEqual('Windstorm');
     });
     ```
   - Open the ~/Projects/heroes folder in a Terminal
   - Run the unit tests
     ```
     ng test
     ```
   - Change the test to make it pass
     - Also modify the title of the test to match what you changed
   - Stop the test by pressing Ctrl-C in the Terminal window
 - Add an e2e test: Make sure your hero is shown
   - Open e2e/src/app.po.ts
   - Add a new function below the existing function getTitleText()
     ```
     getSubTitleText(): Promise<string> {
       return element(by.css('h2')).getText() as Promise<string>;
     }
     ```
   - Open e2e/src/app.e2e-spec.ts
   - Add a new test below the existing test ''should display welcome message'
     ```
     it('should display hero', () => {
       page.navigateTo();
       expect(page.getSubTitleText()).toMatch('.*Details');
     });
     ```
   - Run the e2e tests
     ```
     ng e2e
     ```
 - Commit and synchronize your changes
 - [Format with the UppercasePipe](https://angular.io/tutorial/toh-pt1#format-with-the-uppercasepipe)
   - Change the first line in src/app/heroes/heroes.component.html
   - Leave the other two lines unchanged
 - Rerun the unit and e2e tests to make sure they still pass
 - Commit and synchronize your changes

## Day 6: Edit your Hero :pencil2:
Today we will make our hero editable and learn about the development tools built into your web browser.
 - Run your app in the terminal
 - Open the development tools in the browser where your app is running
   - Chrome
     - Press Option-Command-I (Mac) or Ctrl-Shift-I (Windows)
   - Safari
     - Go to Preferences... Advanced
       - Select: Show Develop menu in menu bar
     - Press Option-Command-I (Mac) or Ctrl-Shift-I (Windows)
 - Follow the [instructions here](https://angular.io/tutorial/toh-pt1#edit-the-hero)
   - Make sure to read them carefully
   - Refactoring means changing your code to make it better
   - The error message may show up in your Terminal window instead of the development tools console
 - As always: Commit and synchronize your changes
 
## Day 7: Rinse and Repeat :feet:
We learned a LOT during the last two weeks!
 - Reread [Week 1: Get Started](https://github.com/phaze9/SummerOfCode/blob/master/Week%201.md) :construction:
   - In the first week we installed and learned about the tools we need.
   - Make sure you know the basics by :heart:
 - Reread [Week 2: Start Coding](https://github.com/phaze9/SummerOfCode/blob/master/Week%202.md) :vibration_mode:
   - In the second week we started working on our app.
   - Make sure you now how to run the app as well as the unit and e2e tests.
   
