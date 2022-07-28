# LABORATORY-KEYCLOAK

This project show how to setup a keycloak using docker-compose and how to use it with a tutorial with images at every steps. The image of the container come from the docker cloud. I use the images **jboss/keycloak** for the keycloak and **postgres** for the database.

## What is keycloak and why to use it ?

*Keycloak is an open-source identity and access management tool for adding authentication to modern applications and services. You can easily set up your application’s login/logout, protected routes and identity management without much work on your part. Once logged-in to Keycloak, users don't have to login again to access a different application.*

## How to use

#### Access the admin console

First we need to start the server keycloak and the database that will keep our users:

```bash
$ npm run start
```

Once the server and the database is running, start your browser and browse to http://localhost:8080/

You should be redirect to the following page:

![Alt text](Documentation/1.png?raw=true "Documentation")

Click on **Administration Page** for accessing the login page for the admin console.

![Alt text](Documentation/2.png?raw=true "Documentation")

The password are inside the `env` folder in the `.env.development` file under:
```yml
KEYCLOAK_USER=admin
KEYCLOAK_PASSWORD=test
```

Fill up **admin** for the username and **test** for the password. You should be redirected to the admin console.

![Alt text](Documentation/3.png?raw=true "Documentation")

#### Create a realm

The first step is to create **a realm**.

*Definition: A realm manages a set of users, credentials, roles, and groups. A user belongs to and logs into a realm. Realms are isolated from one another and can only manage and authenticate the users that they control.*

Hover on the left top scrolldown where **Master** is written. A menu should appear, inviting you to create a realm. Click on the button `Add Realm`.

![Alt text](Documentation/4.png?raw=true "Documentation")

On the new page, enter a name for the realm. It can be anything. Finish the creation by clicking on the button `Create`.

![Alt text](Documentation/5.png?raw=true "Documentation")

You should be redirected to the previous page but the realm will be the one you just created.

#### Creating an user for the realm

Click on **users** in the left menu.

*Definition: Users are entities that are able to log into your system. They can have attributes associated with themselves like email, username, address, phone number, and birth day. They can be assigned group membership and have specific roles assigned to them.*

![Alt text](Documentation/6.png?raw=true "Documentation")

Click on the button `Add user` on the right corner.

![Alt text](Documentation/7.png?raw=true "Documentation")

Fill up the **username**, **firstname** and **lastname** and click on `Save`.

For example:
```
username: myuser
firstname: FirstName
lastname: LastName
```

![Alt text](Documentation/8.png?raw=true "Documentation")

Once save, the tabs should have change and you should be able to see a new tab named `Credentials`. Click on it for creating a password for the user.

Enter a new password and the confirmation password matching it. Turn temporary to off so we are not ask to enter a new password upon the first connection.

For example:
```
password: test
```

Once done, click on the button `Set Password`.

![Alt text](Documentation/9.png?raw=true "Documentation")

Click on the red button `Set Password` for confirming.

#### Accessing the account page of the user

Click on the menu **Client** on the left menu.

![Alt text](Documentation/14.png?raw=true "Documentation")

You should see the link of the **account console**. Right click and open the link in a new tab.

You should be redirect to a login page. Enter the credential of the user we just created. In my case, the username will be **myuser** and my password **test**

![Alt text](Documentation/15.png?raw=true "Documentation")

From this panel, I can modify my information, see the application I am log on and with what device.

#### Accessing and allowing the register

For allowing the register, we need to first activate it.
For doing so, click on the **Realm Setting** menu on the left and take the second tabs **login**.

Activate the first option `User Registration`.

![Alt text](Documentation/16.png?raw=true "Documentation")

You should now see at the bottom of the login, a new option `register`.

![Alt text](Documentation/17.png?raw=true "Documentation")

Now, any person can register on your keycloak by following the following form.
The user can be seen in the admin panel.

![Alt text](Documentation/18.png?raw=true "Documentation")

## Links

* [https://www.baeldung.com/spring-boot-keycloak](https://www.baeldung.com/spring-boot-keycloak)
* [https://blog.logrocket.com/implement-keycloak-authentication-react/](https://blog.logrocket.com/implement-keycloak-authentication-react/)
* [https://www.keycloak.org/docs/latest/server_admin/#:~:text=A%20realm%20manages%20a%20set,Keycloak%20to%20authenticate%20a%20user.](https://www.keycloak.org/docs/latest/server_admin/#:~:text=A%20realm%20manages%20a%20set,Keycloak%20to%20authenticate%20a%20user.)
