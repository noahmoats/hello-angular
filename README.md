# hello-angular

This is how Angular is used in this app.When the user is on the main page, "hi there, tom tom" is displayed. "tom tom" is part of an object that comes from the user.json file, which can be seen on the /user page. index.js maps to that file with this bit of code:

app.get('/user', function (req, res) {

    res.sendFile('/user.json', { root: __dirname });

});

app.controller('MainController', function ($scope, $http) {
            $scope.user = null;

            $http.get('/user')
                .then(response => {
                    console.log(response.data);

                    $scope.user = response.data;
                });

        });
doing this will then display the 'name' with <h3 id="user-greeting">and hi there, {{ user.name }}</h3>. An input box is created with the line <input ng-model="user.name"> and updates the 'name' live on the page without a refresh of the page. However, the data is not updated and saved in user.json, so anything new put in the box is gone when the page is refreshed.

# Link to app on heroku https://hello-angularr.herokuapp.com/
