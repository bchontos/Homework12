First we will be setting up the connection to the server
    *requiring all the npm packages we need
    *setting up access port to the server
    *syncing to our database then promping the user with a message apon success

Setting up HTML routs
    * frist need to require path to send html files to their routes
    *requiring custom middleware to check if the user is logged in
    *then setting up our get requests
        * first get request is sending them to the signup page
        * second get request is sending the user to the members page if they already set up an account
        * third request is sending the user to the signup page if they try to login and they dont have an account

Setting up API routs
    * first thing is to require all dependencies that will be used
    *the first app.post is allowing us to authenticate with our local stragtegy and let go to the member page otherwise it will send an error
    * api/signup function allows us to create a new user and password and if the user successfully creates an account will take them to the login screen
    * /logout logs out the user and redirects them to the main page
    * /api/user_data will get the data of the user and will be displayed as a json object. else send back user email and id

Signup JS
    * first we are getting the document ready function so that the page does not refresh on it's own
    * next we are getting references with var for the input and form
    * signUpForm allows us to validate that the email and password and not left blank then we are running the signUpUser function
    * signUpUser allows us to post the email and password into the data base so we can store it for them in our database, if there is an error somewhere in the signup it will redirect to handleLoginErr function
    * handleLoginErr will show us alert code 500 which means internal server error

Members JS
    * this function allows us to figure out what user is logged in and updates the html on the page

Login JS
    * first we are getting the document ready function so that the page does not refresh on it's own
    * once the form is submitted there validate that an email and password is entered
    * loginUser takes the input of email and password and makes them into a string, the function call does a post request to the api/login route if successful and then takes the user to the members page

User JS
    * first we are requiring bcryptjs for use of password hashing
    * start off by creating our user model
    * defining email and saying the email cant be null and validating if an email was put in correctly
    * defining password and saying the password cant be null
    * create own method that will check if unhashed password was entered by the user can be compared to the hashed password in the database
    
Index JS
    * In this file, we are requiring the modules we're going to be using. Then, we're reading the configuration specific to our current Node environment. If we don't have a Node environment defined, we're defaulting to development. Then, we are establishing a connection with our database, after which we read our models folder, discovering and importing any and all the models in it, adding them to the db object and applying relationships between the models, if such relationships exist

Passport JS
    * first we are setting up our variables
    * telling passport that we want to login with either username or email along with password
    * then our user will sign un using email it will run through the database and find the user ID with the matching email
    * if there is a user with no email when they enter it will return a message saying incorrect email
    * if the user enters the incorrect password than what is saved on the database it will return a message saying incorrect password

isAuthenticated JS
    * this is a middleware that restricts a user from visting the website if not logged in 

