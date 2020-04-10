# angular8-repo
Angular 8 

#Git Repository: 
git@github.com:Ravikumar-Pothannagari/angular8-repo.git

#Angular 8 Tutorial
Angular community has released its latest version which is known as Angular 8. 
If you are familiar with previous version of Angular, it will not be difficult for you. 
You can easily upgrade your Angular CLI to version 8. 

#What is Angular 8?

Angular 8 is a client-side TypeScript based framework which is used to create dynamic web applications. 
It is very similar to its previous versions except having some extensive features.


#Note: 
Dynamic web applications are simply dynamic websites 
i.e. www.gmail.com, www.yahoo.com, etc. which has tendency to change data/information with respect to 3 parameters:

 > Time-to-time (eg. news update webs applications)
 > Location-to-location (eg. Weather-report web applications)
 > User-to-user (eg. Gmail, Facebook type applications)




# New Features of Angular 8

The Angular community has released its latest version Angular 8 with an impressive list of changes and improvements including the much awaited Ivy compiler as an opt-in feature.

These are the most prominent features of Angular 8:

    Angular 8 supports TypeScript 3.4
    Angular 8 supports Web Workers
    The new compiler for Angular 8 is Ivy Rendering Engine
    Angular 8 provides dynamic imports for lazy-loaded modules.
    Improvement of ngUpgrade


# TypeScript 3.4

Angular 8 supports TypeScript 3.4 and it is required to run your Angular 8 project. 
So you have to upgrade your TypeScript version to 3.4.

> Web workers class

JavaScript is single threaded, so it is common for more critical tasks like data calls to take place asynchronously. 
Web Workers facilitates you to run the CPU intensive computations in the background thread, freeing the main thread to update the user interface.

Web workers can also be helpful, if your application is unresponsive while processing data.

If you want to outsource such a calculation to a background, we must first create the web worker using the Angular CLI. 
  
  > ng generate worker n-queens




More about Ivy and Bazel

Ivy is the new rendering engine and Bazel is the new build system. Both are ready for proper use with Angular 8. The preview of these two should be available shortly. Ivy is a new compiler/runtime of Angular and Angular 8 is a first release to offer a switch to opt-in into Ivy officially.

Ivy is supposed to be a by default rendering engine in Angular version 9.

Bazel provides one of the newest features of Angular 8 as a possibility to build your CLI application more quickly.

The main advantages of Bazel are:

    The incremental build and tests.
    It provides a chance to make your backends and frontends with a same tool.
    It has a possibility to have remote builds and cache on the build farm.

Dynamic imports for lazy-loaded modules

Angular 8 facilitates you to use standard dynamic import syntax instead of a custom string for lazy-loaded modules.

It means lazy-loaded import that looked like this:

    { path: '/student', loadChildren: './student/student.module#StudentModule' }  

Will be looked like this:

    { path: `/student`, loadChildren: () => import(`./student/student.module`).then(s => s.StudentModule) }  

# Improved Angular CLI Workflow

The Angular CLI is continuously improving. Now, the ng build, ng test and ng run are equipped by 3rd-party libraries and tool. For example, AngularFire already makes use of these new capabilities with a deploy command.

# Prerequisite for Angular 8 tutorial

    You must have installed Node.js version > 10. NPM will be updated also because it will be used by default. Here, I am using Node version 12.4.0
    You must have installed MongoDB on your system. You can see how to install MongoDB. Click here...

# Workflow of Angular 8 Tutorial

Here, we will create two separate projects:

One for front end (in Angular) and one for backend (in Node.js | Express | MongoDB). We will also create a backend API which will be used by frontend.

Here, we use the following technologies:

    Node: 12.4.0
    Angular CLI: 8.0.2
    NPM: v12.4.0
    MongoDB shell version v4.0.10
    MongoDB version v4.0.10
    Windows 10
  
#Note: 
  You can check your node, angular, npm, and mongoDB versions by using the following commands: 
  
 
    To check Node and Angular CLI version, use ng --version command.
    To check npm version, use node -v command.
    To check MongoDB version, use mongod --version command.
    To check MongoDB shell version, use mongo --version command.


# Create an Angular 8 project

	> Let's create an Angular 8 project by using the following command: 
	
	ng new angular8project
	
	C:\Users\RavikumarPothannagar\Documents\GitHub\angular8-repo>ng new angular8project
		? Would you like to add Angular routing? Yes
		? Which stylesheet format would you like to use? CSS
	

	C:\Users\RavikumarPothannagar\Documents\GitHub\angular8-repo>cd angular8project

	C:\Users\RavikumarPothannagar\Documents\GitHub\angular8-repo\angular8project>code .	
	
# Install Bootstrap 4 CSS framework

	Use the following command to install bootstrap in your project.

   > npm install bootstrap --save
   
   > Now, add the following code inside the angular.json file.
   
    "styles": [  
       "src/styles.css",  
       "./node_modules/bootstrap/dist/css/bootstrap.min.css"  
     ],  
	 
	The above CSS is used that we can use the bootstrap classes inside any file.

    Start the Angular development server using the following command.
	
	> ng serve -o
	
	>> http://localhost:4200/
	
	> Please run next command `npm update`
	
	
# Project Description

In this project, we will facilitate users:

    To enter their ProductName, Product Description, and ProductPrice to a form and submit the form.
    
	Validate the form against values. If values are incorrect, then it will be validated at the frontend and form will not be submitted.
    
	If all values are correct, send the form to the Node.js backend API.
    
	Store the values inside the MongoDB database.
    
	Show the data on the frontend.
    
	Facilitates users to edit and delete the data also.
    
	Show the data on the MongoD CLI.
    
	Show the data on MongoDB Compass Community (a GUI of MongoDB database.).


# Generate Angular Components

We are going to make a CRUD operation to create, read, and update data. So, we will create three components.

Use the following command to generate 3 Angular Components:

  >  ng g c product-add --skipTests=true  
  >  ng g c product-get --skipTests=true  
  >  ng g c product-edit --skipTests=true


# Note: 
	The "spec" command is deprecated in Angular 8. You have to use "skipTests" instead.


All the above 3 components are automatically added to app.module.ts file. 
Now, we have to configure the routing of angular components inside an app-routing.module.ts file.

You can check the app-routing.module.ts file inside the src >> app folder in your project file. It is created because when we install an angular app, we permit angular cli to generate the routing file for us.

Now, write the following code inside an app-routing.module.ts file:	

# app-routing.module.ts
---------------------------------------------------------------------------------------------
    // app-routing.module.ts  
    import { NgModule } from '@angular/core';  
    import { Routes, RouterModule } from '@angular/router';  
    import { ProductAddComponent } from './product-add/product-add.component';  
    import { ProductEditComponent } from './product-edit/product-edit.component';  
    import { ProductGetComponent } from './product-get/product-get.component';  
    const routes: Routes = [  
      {  
        path: 'product/create',  
        component: ProductAddComponent  
      },  
      {  
        path: 'edit/:id',  
        component: ProductEditComponent  
      },  
      {  
        path: 'products',  
        component: ProductGetComponent  
      }  
    ];  
    @NgModule({  
      imports: [RouterModule.forRoot(routes)],  
      exports: [RouterModule]  
    })  
    export class AppRoutingModule { }  
---------------------------------------------------------------------------------------------

# app.component.html
  
   Now, you can see inside the app.component.html file that directive is there. 
   This directive helps us to render the different component based on the route URI.
   
# Create Angular Navigation
---------------------------------------------------------------------------------------------
    <nav class="navbar navbar-expand-sm bg-light">  
      <div class="container-fluid">  
        <ul class="navbar-nav">  
          <li class="nav-item">  
            <a routerLink="product/create" class="nav-link" routerLinkActive="active">  
              Create Product  
            </a>  
          </li>  
          <li class="nav-item">  
            <a routerLink="products" class="nav-link" routerLinkActive="active">  
              Products  
            </a>  
          </li>   
        </ul>  
      </div>  
    </nav>  
    <div class="container">  
      <router-outlet></router-outlet>  
    </div>  
---------------------------------------------------------------------------------------------

# Install Angular Routing Progress Indicator

Type the following command to install the ng2-slim-loading-bar library.

	> npm install ng2-slim-loading-bar --save


If you have installed third-party packages right now, then it is not compatible with Angular 8. 
To solve the problem between Angular 8 and third-party packages, you have to install the following library.

	> npm install rxjs-compat --save 

Now, import the SlimLoadingBarModule inside an app.module.ts file.

#app.module.ts

---------------------------------------------------------------------------------------------
import { SlimLoadingBarModule } from 'ng2-slim-loading-bar';  
imports: [  
    ...  
    SlimLoadingBarModule  
],
 
---------------------------------------------------------------------------------------------
# src > styles.css file

Now, include the styling that comes with the library inside src >> styles.css file.

    @import "../node_modules/ng2-slim-loading-bar/style.css"; 

---------------------------------------------------------------------------------------------

# Adding Router Events

Angular RouterModule gives us the following event modules.

    NavigationStart
    NavigationEnd
    NavigationError
    NavigationCancel
    Router
    Event

---------------------------------------------------------------------------------------------
	
# app.component.ts

Now, write the following code inside the app.component.ts file.	


    import { Component } from '@angular/core';  
    import {SlimLoadingBarService} from 'ng2-slim-loading-bar';  
    import { NavigationCancel,  
     Event,  
            NavigationEnd,  
            NavigationError,  
            NavigationStart,  
            Router } from '@angular/router';  
    @Component({  
      selector: 'app-root',  
      templateUrl: './app.component.html',  
      styleUrls: ['./app.component.css']  
    })  
    export class AppComponent {  
      title = 'angular8tutorial';  
      constructor(private loadingBar: SlimLoadingBarService, private router: Router) {  
        this.router.events.subscribe((event: Event) => {  
          this.navigationInterceptor(event);  
        });  
      }  
      private navigationInterceptor(event: Event): void {  
        if (event instanceof NavigationStart) {  
          this.loadingBar.start();  
        }  
        if (event instanceof NavigationEnd) {  
          this.loadingBar.complete();  
        }  
        if (event instanceof NavigationCancel) {  
          this.loadingBar.stop();  
        }  
        if (event instanceof NavigationError) {  
          this.loadingBar.stop();  
        }  
      }  
    }  


---------------------------------------------------------------------------------------------
In the above code, we have specified in Angular application that when the user navigates from one component to another component, it will show the progress result.

When the user clicks the other route, angular progress indicator start showing, and when the navigation is complete, it will stop displaying. So, it is kind of UX for the user.

The above code intercepts the routing event and add the loading bar component to every route, so that we can see the routing indication every time when we change the routes.

We have to add the ng2-slim-loading-bar directive inside the app.component.html file at the top of the page.

# app.component.html

<!-- app.component.html -->  
<ng2-slim-loading-bar color="blue"></ng2-slim-loading-bar>  
<nav class="navbar navbar-expand-sm bg-light">  
  <div class="container-fluid">  
    <ul class="navbar-nav">  
      <li class="nav-item">  
        <a routerLink="product/create" class="nav-link" routerLinkActive="active">  
          Create Product  
        </a>  
      </li>  
      <li class="nav-item">  
        <a routerLink="products" class="nav-link" routerLinkActive="active">  
          Products  
        </a>  
      </li>   
    </ul>  
  </div>  
</nav>  
<div class="container">  
  <router-outlet></router-outlet>  
</div> 

---------------------------------------------------------------------------------------------

# Add Bootstrap Form

Add the following bootstrap 4 form Inside the product-add.component.html file.

    <div class="card">  
      <div class="card-body">  
        <form>  
          <div class="form-group">  
            <label class="col-md-4">Product Name</label>  
            <input type="text" class="form-control" />  
          </div>  
          <div class="form-group">  
            <label class="col-md-4">Product Description </label>  
            <textarea class="form-control" rows = 7 cols = "5"></textarea>  
          </div>  
          <div class="form-group">  
            <label class="col-md-4">Product Price</label>  
            <input type="text" class="form-control" />  
          </div>  
          <div class="form-group">  
            <button type="submit" class="btn btn-primary">Create Product</button>  
          </div>  
        </form>  
      </div>  
    </div> 

---------------------------------------------------------------------------------------------

Open the localhost browser and see the output. It will look like the image given below. 

C:\Users\RavikumarPothannagar\Documents\GitHub\angular8-repo\angular8project> ng serve -o

http://localhost:4200/product/create

---------------------------------------------------------------------------------------------

#Add Angular 8 Form Validation

---------------------------------------------------------------------------------------------
Here, we use reactive form module to add the validation in our form. Import the ReactiveFormsModule inside the app.module.ts file.

    import { ReactiveFormsModule } from '@angular/forms';  
    imports: [  
        ...  
        ReactiveFormsModule  
    ],  

---------------------------------------------------------------------------------------------

Here, you need to aware that it is not a template driven form, so you need to change in the app.component.ts file.

Here, we have to import the FormGroup, FormBuilder, Validators modules from @angular/forms and create a constructor and instantiate the FormBuilder.

So, write the following code inside the product-add.component.ts file.

# product-add.component.ts

    import { Component, OnInit } from '@angular/core';  
    import { FormGroup,  FormBuilder,  Validators } from '@angular/forms';  
    @Component({  
      selector: 'app-product-add',  
      templateUrl: './product-add.component.html',  
      styleUrls: ['./product-add.component.css']  
    })  
    export class ProductAddComponent implements OnInit {  
      angForm: FormGroup;  
      constructor(private fb: FormBuilder) {  
        this.createForm();  
      }  
      createForm() {  
        this.angForm = this.fb.group({  
          ProductName: ['', Validators.required ],  
          ProductDescription: ['', Validators.required ],  
          ProductPrice: ['', Validators.required ]  
        });  
      }  
      ngOnInit() {  
      }  
    }  
	
---------------------------------------------------------------------------------------------

# product-add.component.html	

Here, we use form builder to handle all the validation. Now, in that constructor, we have to create a form with the validation rules. In our example, there are three fields. If the input text is empty, then it will give an error, and we need to display that error.

Now, write the following code inside the product-add.component.html file.




    <div class="card">  
      <div class="card-body">  
        <form [formGroup]="angForm" novalidate>  
          <div class="form-group">  
            <label class="col-md-4">Product Name</label>  
            <input type="text" class="form-control"   
              formControlName="ProductName"   
              #ProductName />  
          </div>  
          <div *ngIf="angForm.controls['ProductName'].invalid && (angForm.controls['ProductName'].dirty || angForm.controls['ProductName'].touched)" class="alert alert-danger">  
            <div *ngIf="angForm.controls['ProductName'].errors.required">  
              Product Name is required.  
            </div>  
          </div>  
          <div class="form-group">  
            <label class="col-md-4">Product Description </label>  
            <textarea class="form-control" rows = 7 cols = "5"  
            formControlName="ProductDescription"   
            #ProductDescription></textarea>  
          </div>  
          <div *ngIf="angForm.controls['ProductDescription'].invalid && (angForm.controls['ProductDescription'].dirty || angForm.controls['ProductDescription'].touched)" class="alert alert-danger">  
            <div *ngIf="angForm.controls['ProductDescription'].errors.required">  
              Product Description is required.  
            </div>  
          </div>  
          <div class="form-group">  
            <label class="col-md-4">Product Price</label>  
            <input type="text" class="form-control"   
              formControlName="ProductPrice"   
              #ProductPrice  
            />  
          </div>  
          <div *ngIf="angForm.controls['ProductPrice'].invalid && (angForm.controls['ProductPrice'].dirty || angForm.controls['ProductPrice'].touched)" class="alert alert-danger">  
            <div *ngIf="angForm.controls['ProductPrice'].errors.required">  
              Product Price is required.  
            </div>  
          </div>  
          <div class="form-group">  
            <button type="submit" class="btn btn-primary"  
            [disabled]="angForm.pristine || angForm.invalid" >  
              Create Product  
            </button>  
          </div>  
        </form>  
      </div>  
    </div>  

---------------------------------------------------------------------------------------------

# Configure the HttpClientModule

# app.module.ts

The Front-end applications always need HTTP protocol to communicate with the backend services. Modern browsers support two different APIs for making HTTP requests: the javaHttpRequest interface and the fetch() API.

Import the HttpClientModule inside an app.module.ts file.

    // app.module.ts  
    import { HttpClientModule } from '@angular/common/http';  
    imports: [  
       ...  
        HttpClientModule  
     ],  
	 
---------------------------------------------------------------------------------------------
# Create a model file


Inside the src >> app folder, create one file called Product.ts and add the following code.

    export default class Product {  
      ProductName: string;  
      ProductDescription: string;  
      ProductPrice: number;  
    }  
	
---------------------------------------------------------------------------------------------
# Create an Angular Service file

	Type the following command to generate the service file.

    > ng 	g service products --skipTests=true  

	After creation, it will look like this:

    import { Injectable } from '@angular/core';  
    @Injectable({  
      providedIn: 'root'  
    })  
    export class ProductsService {  
      
      constructor() { }  
    }  

# app.module.ts

Now, import the products.service.ts file into the app.module.ts file.

    import { ProductsService } from './products.service';  
    providers: [ ProductsService ],  
	
---------------------------------------------------------------------------------------------


# Submit the data to the node server
# products.service.ts

Now, we have to write the code that will send the HTTP POST request with the data to the Node.js server and after that save the data into the MongoDB database.

Write the following code inside the products.service.ts file.

    import { Injectable } from '@angular/core';  
    import { HttpClient } from '@angular/common/http';  
    @Injectable({  
      providedIn: 'root'  
    })  
    export class ProductsService {  
      uri = 'http://localhost:4000/products';  
      constructor(private http: HttpClient) { }  
      addProduct(ProductName, ProductDescription, ProductPrice) {  
        const obj = {  
          ProductName,  
          ProductDescription,  
          ProductPrice  
        };  
        console.log(obj);  
        this.http.post(`${this.uri}/add`, obj)  
            .subscribe(res => console.log('Done'));  
      }  
    }  

Note: Here, we have defined our backend API URL, but we have not created any backend yet. Let's create it.

---------------------------------------------------------------------------------------------
# product-add.component.html

Now, we have to add the click event to the Add Product Button. So, add the following code inside the product-add.component.html file.

    <div class="form-group">  
            <button (click) = "addProduct(ProductName.value, ProductDescription.value, ProductPrice.value)" type="submit" class="btn btn-primary"  
            [disabled]="angForm.pristine || angForm.invalid" >  
              Create Product  
            </button>  
    </div> 
	
---------------------------------------------------------------------------------------------
# product-add.component.ts

Now, add the addProduct() function inside the product-add.component.ts file. So, write the following code inside the product-add.component.ts file.

    import { Component, OnInit } from '@angular/core';  
    import { FormGroup, FormBuilder, Validators } from '@angular/forms';  
    import { ProductsService } from '../products.service';  
    @Component({  
      selector: 'app-product-add',  
      templateUrl: './product-add.component.html',  
      styleUrls: ['./product-add.component.css']  
    })  
    export class ProductAddComponent implements OnInit {  
      
      angForm: FormGroup;  
      constructor(private fb: FormBuilder, private ps: ProductsService) {  
        this.createForm();  
      }  
      createForm() {  
        this.angForm = this.fb.group({  
          ProductName: ['', Validators.required ],  
          ProductDescription: ['', Validators.required ],  
          ProductPrice: ['', Validators.required ]  
        });  
      }  
      addProduct(ProductName, ProductDescription, ProductPrice) {  
        this.ps.addProduct(ProductName, ProductDescription, ProductPrice);  
      }  
      ngOnInit() {  
      }  
    }  

---------------------------------------------------------------------------------------------
# Create a Node.js backend API


Create a folder called the api inside an angular root folder, and go inside that folder. 
It will be the complete separate project from your Angular project. So, its node_modules folders are different from the Angular project.

Open the terminal inside the api folder and type the following command. 
It will generate the package.json file using NPM.

	C:\Users\RavikumarPothannagar\Documents\GitHub\angular8-repo\angular8project> cd api

	C:\Users\RavikumarPothannagar\Documents\GitHub\angular8-repo\angular8project\api>

    > npm init -y
	
	
	Install the following node specific modules.

    > npm install express body-parser cors mongoose --save
	
	
	Install the nodemon server, it will facilitate you to not to start node server every time you make changes it. 
	It restarts the node.js server automatically.

    > npm install nodemon --save-dev
	
# server.js	
	Now, inside the api folder, create one file called the server.js file. Add the following code inside the server.js file.
	
	
	    const express = require('express'),  
        path = require('path'),  
        bodyParser = require('body-parser'),  
        cors = require('cors'),  
        mongoose = require('mongoose');  
        const app = express();  
        let port = process.env.PORT || 4000;  
        const server = app.listen(function(){  
            console.log('Listening on port ' + port);  
        });  
		
---------------------------------------------------------------------------------------------
	Now, connect to the MongoDB database with our node express application.

If you have not installed a MongoDB database, then install it and then start the mongodb server using the following command.

# How to Install MongoDB

 > mongod
 
 # How to install MongoDB on Windows
 
 Firstly you will have to download the latest release of MongoDB:

 How to download MongoDB

You can download an appropriate version of MongoDB which your system supports, from the link "http://www.mongodb.org/downloads" to install the MongoDB on Windows. You should choose correct version of MongoDB acording to your computer's Window. If you are not sure what Window version are you using, open your command prompt and
execute this command:

    C:\ wmic os get osarchitecture  

OSArchitecture 
64 bit
C:\ >

Note: MongoDB does not support Window XP.




# How to install the downloaded file

In Window explorer, locate the downloaded MongoDB msi file, double click on that file and follow the instructions appears on the screen. These instructions will guide you to complete the installation process.
Note: If you want to move the MongoDB folder from default position to another position, it is necessary to issue the move command as an administrator. let us take an example to move the folder to C : \mongodb:

  Select Start Menu > All Programs > Accessories   

You can install MongoDB in any folder because it is self contained and does not have any other system dependency.

# How to set up the MongoDB environment

A data directory is required in MongoDB to store all the information. Its by default data directory path is \data\db. you can create this folder by command prompt.

    md\data\db  

# For example:

If you want to start MongoDB, run mongod.exe

You can do it from command prompt.

    C:\Program Files\MongoDB\bin\mongod.exe  

This will start the mongoDB database process. If you get a message "waiting for connection" in the console output, it indicates that the mongodb.exe process is running successfully.

# For example:

When you connect to the MongoDB through the mongo.exe shell, you should follow these steps:

    Open another command prompt.
    At the time of connecting, specify the data directory if necessary.

Note: If you use the default data directory while MongoDB installation, there is no need to specify the data directory.

# For example:

    C:\mongodb\bin\mongo.exe  

If you use the different data directory while MongoDB installation, specify the directory when connecting.

# For example:

    C:\mongodb\bin\mongod.exe-- dbpath d:\test\mongodb\data  

If you have spaces in your path, enclose the entire path in double space.

# For example:

    C:\mongodb\bin\mongod.exe-- dbpath  "d: \ test\mongodb\data"  
 
 
 C:\Users\RavikumarPothannagar\Documents\GitHub\angular8-repo\mongodb\data
 
 # run mongod
 C:\Users\RavikumarPothannagar\Desktop\IBM\Personal\MongoDB\mongodb-win32-x86_64-2012plus-4.2.5\bin>mongod.exe --dbpath "C:\Users\RavikumarPothannagar\Documents\GitHub\angular8-repo\mongodb\data"
 
 
 Now, we have connected to the database.
---------------------------------------------------------------------------------------------

# DB.js

Create one file called DB.js inside the api root project folder. Write the following code inside a DB.js file.

    module.exports = {  
      DB: 'mongodb://localhost:27017/ng8crud'  
    };  

Import this DB.js file inside our server.js file and use the mongoose library to set up the database connection with MongoDB. Write a following code inside the server.js file to connect our MongoDB application to the Node.js server.



# server.js

Import this DB.js file inside our server.js file and use the mongoose library to set up the database connection with MongoDB. Write a following code inside the server.js file to connect our MongoDB application to the Node.js server.

    const express = require('express'),  
        path = require('path'),  
        bodyParser = require('body-parser'),  
        cors = require('cors'),  
        mongoose = require('mongoose'),  
        config = require('./DB');  
        mongoose.Promise = global.Promise;  
        mongoose.connect(config.DB, { useNewUrlParser: true }).then(  
          () => {console.log('Database is connected') },  
          err => { console.log('Can not connect to the database'+ err)}  
        );  
        const app = express();  
        app.use(bodyParser.json());  
        app.use(cors());  
        const port = process.env.PORT || 4000;  
        const server = app.listen(port, function(){  
         console.log('Listening on port ' + port);  
        });  


	Save this server.js file and go to the terminal and start the node server using the following command.

    > npm start   

	So, right now, there are three servers running:

    Angular Development Server
    Node.js Server
    MongoDB server

	Angular Server: > ng serve -o
	Node.js Server: > npm start
	MongoDB server: > mongod.exe --dbpath "db/data"
	

---------------------------------------------------------------------------------------------
# api > routes >

# api > models >

Create model and routes for your application

Now, we have to create two folders inside the api root folder called routes and models.

Let's create one model called Product.js in models folder having the following code.

    const mongoose = require('mongoose');  
    const Schema = mongoose.Schema;  
    // Define collection and schema for Product  
    let Product = new Schema({  
      ProductName: {  
        type: String  
      },  
      ProductDescription: {  
        type: String  
      },  
      ProductPrice: {  
        type: Number  
      }  
    },{  
        collection: 'Product'  
    });  
    module.exports = mongoose.model('Product', Product);


Here, we have defined our schema for the Product collection. 
We have three fields called ProductName, ProductDescription, ProductPrice.
	
---------------------------------------------------------------------------------------------
# product.route.js

In the routes folder, create one file called the product.route.js.

Write the following CRUD code inside the product.route.js file.


    const express = require('express');  
    const app = express();  
    const productRoutes = express.Router();  
    // Require Product model in our routes module  
    let Product = require('../models/Product');  
    // Defined store route  
    productRoutes.route('/add').post(function (req, res) {  
      let product = new Product(req.body);  
      product.save()  
        .then(product => {  
          res.status(200).json({'Product': 'Product has been added successfully'});  
        })  
        .catch(err => {  
        res.status(400).send("unable to save to database");  
        });  
    });  
    // Defined get data(index or listing) route  
    productRoutes.route('/').get(function (req, res) {  
      Product.find(function (err, products){  
        if(err){  
          console.log(err);  
        }  
        else {  
          res.json(products);  
        }  
      });  
    });  
    // Defined edit route  
    productRoutes.route('/edit/:id').get(function (req, res) {  
      let id = req.params.id;  
      Product.findById(id, function (err, product){  
          res.json(product);  
      });  
    });  
    //  Defined update route  
    productRoutes.route('/update/:id').post(function (req, res) {  
      Product.findById(req.params.id, function(err, product) {  
        if (!product)  
          res.status(404).send("Record not found");  
        else {  
          product.ProductName = req.body.ProductName;  
          product.ProductDescription = req.body.ProductDescription;  
          product.ProductPrice = req.body.ProductPrice;  
     product.save().then(product => {  
              res.json('Update complete');  
          })  
          .catch(err => {  
                res.status(400).send("unable to update the database");  
          });  
        }  
      });  
    });  
    // Defined delete | remove | destroy route  
    productRoutes.route('/delete/:id').get(function (req, res) {  
        Product.findByIdAndRemove({_id: req.params.id}, function(err, product){  
            if(err) res.json(err);  
            else res.json('Successfully removed');  
        });  
    });  
    module.exports = productRoutes;  


---------------------------------------------------------------------------------------------
# server.js

Now, we have all the CRUD operations set up on the route file; we need to import inside the server.js file.

So, update the server.js file with the following code:

    const express = require('express'),  
        path = require('path'),  
        bodyParser = require('body-parser'),  
        cors = require('cors'),  
        mongoose = require('mongoose'),  
        config = require('./DB');  
       const productRoute = require('./routes/product.route');  
        mongoose.Promise = global.Promise;  
        mongoose.connect(config.DB, { useNewUrlParser: true }).then(  
          () => {console.log('Database is connected') },  
          err => { console.log('Can not connect to the database'+ err)}  
        );  
        const app = express();  
        app.use(bodyParser.json());  
        app.use(cors());  
        app.use('/products', productRoute);  
        const port = process.env.PORT || 4000;  
        const server = app.listen(port, function(){  
         console.log('Listening on port ' + port);  
        });  
		
---------------------------------------------------------------------------------------------
Now, start the node.js server, if you yet not started. If it is already started then let's check the data store functionality.

Test the data store functionality

Now, we will enter some data to test if it is storing or not.

First, open the mongo shell on the 4th tab because all the other three tabs are occupied at the moment.

Use the following command to open mongo shell:

	> mongo
	
	Example :
	> cd C:\Users\RavikumarPothannagar\Desktop\IBM\Personal\MongoDB\mongodb-win32-x86_64-2012plus-4.2.5\bin
	
	> C:\Users\RavikumarPothannagar\Desktop\IBM\Personal\MongoDB\mongodb-win32-x86_64-2012plus-4.2.5\bin\mongo
	
Here, you can use

    > show dbs command to see the databases
    > use database_name command to use the database and db.collection_name.find() to find the query.


	Note: Here, we have used db.collection_name.find().pretty() command to prettify the result only.
	
	Alternative way to see the stored items in database

	You can also use the MongoDB Compass Community to see the databases and entries if we prefer a GUI.

---------------------------------------------------------------------------------------------
# Display the data on the frontend browser 

# product-get.component.html

If you want to display the data on the frontend browser, use the following code inside the product-get.component.html file.

<table class="table table-hover">  
  <thead>  
  <tr>  
      <td>Product Name</td>  
      <td>Product Description</td>  
      <td>Product Price</td>  
      <td colspan="2">Actions</td>  
  </tr>  
  </thead>  
  <tbody>  
      <tr *ngFor="let product of products">  
          <td>{{ product.ProductName }}</td>  
          <td>{{ product.ProductDescription }}</td>  
          <td>{{ product.ProductPrice }}</td>  
          <td><a [routerLink]="['/edit', product._id]" class="btn btn-primary">Edit</a></td>  
          <td><a [routerLink]="" class="btn btn-danger">Delete</a></td>  
      </tr>  
  </tbody>  
</table> 

---------------------------------------------------------------------------------------------
# products.service.ts

Now, we have to write the function inside the products.service.ts file that fetches the products data from the MongoDB database and display at the Angular application.


 getProducts() {  
        return this  
               .http  
               .get(this.uri);  
      } 
	  
---------------------------------------------------------------------------------------------
Include this products.service.ts file and Product.ts file inside the product-get.component.ts file.

Write the following code inside the product-get.component.ts file.


    import { Component, OnInit } from '@angular/core';  
    import Product from '../Product';  
    import { ProductsService } from '../products.service';  
    @Component({  
      selector: 'app-product-get',  
      templateUrl: './product-get.component.html',  
      styleUrls: ['./product-get.component.css']  
    })  
    export class ProductGetComponent implements OnInit {  
      products: Product[];  
      constructor(private ps: ProductsService) { }  
      ngOnInit() {  
        this.ps  
          .getProducts()  
          .subscribe((data: Product[]) => {  
            this.products = data;  
        });  
      }  
    }  

Now, save the file, go to the browser and switch to this URL: http://localhost:4200/products. You will see the following result. 
Now, you have succeeded to fetch data from the database and show to the browser.	
---------------------------------------------------------------------------------------------
# Edit and Update the Data

First, we need to fetch the _id wise data from the MongoDB database and then display that data in the product-edit.component.html file.

Write the following code inside the product-edit.component.ts file. 

#product-edit.component.ts

    import { Component, OnInit } from '@angular/core';  
    import { FormGroup, FormBuilder, Validators } from '@angular/forms';  
    import { ActivatedRoute, Router } from '@angular/router';  
    import { ProductsService } from '../products.service';  
    @Component({  
      selector: 'app-product-edit',  
      templateUrl: './product-edit.component.html',  
      styleUrls: ['./product-edit.component.css']  
    })  
    export class ProductEditComponent implements OnInit {  
      angForm: FormGroup;  
     product: any = {};  
      constructor(private route: ActivatedRoute, private router: Router, private ps: ProductsService, private fb: FormBuilder) {  
          this.createForm();  
     }  
      createForm() {  
        this.angForm = this.fb.group({  
          ProductName: ['', Validators.required ],  
          ProductDescription: ['', Validators.required ],  
          ProductPrice: ['', Validators.required ]  
        });  
      }  
      ngOnInit() {  
        this.route.params.subscribe(params => {  
            this.ps.editProduct(params['id']).subscribe(res => {  
              this.product = res;  
          });  
        });  
      }  
    }  

Here, when the product-edit component.ts render, it will call the ngOnInit method and send an HTTP request to the node server and fetch the data from an _id to display inside the product-edit component.html file.

---------------------------------------------------------------------------------------------

Now, inside the products.service.ts file, we need to code the editProduct function to send an HTTP request.

# products.service.ts

    import { Injectable } from '@angular/core';  
    import { HttpClient } from '@angular/common/http';  
    @Injectable({  
      providedIn: 'root'  
    })  
    export class ProductsService {  
      uri = 'http://localhost:4000/products';  
      constructor(private http: HttpClient) { }  
      addProduct(ProductName, ProductDescription, ProductPrice) {  
        console.log(ProductName, ProductDescription, ProductPrice);  
        const obj = {  
          ProductName,  
          ProductDescription,  
          ProductPrice  
        };  
        this.http.post(`${this.uri}/add`, obj)  
            .subscribe(res => console.log('Done'));  
      }  
      getProducts() {  
        return this  
               .http  
               .get(`${this.uri}`);  
      }  
      editProduct(id) {  
        return this  
                .http  
                .get(`${this.uri}/edit/${id}`);  
        }  
    }  
---------------------------------------------------------------------------------------------
At last, write the form inside the product-edit.component.html file.


    <!-- product-edit.component.html -->  
    <div class="card">  
      <div class="card-body">  
        <form [formGroup]="angForm" novalidate>  
          <div class="form-group">  
            <label class="col-md-4">Product Name</label>  
            <input type="text" class="form-control"   
              formControlName="ProductName"   
              #ProductName   
              [(ngModel)] = "product.ProductName"/>  
          </div>  
          <div *ngIf="angForm.controls['ProductName'].invalid && (angForm.controls['ProductName'].dirty || angForm.controls['ProductName'].touched)" class="alert alert-danger">  
            <div *ngIf="angForm.controls['ProductName'].errors.required">  
              Product Name is required.  
            </div>  
          </div>  
          <div class="form-group">  
            <label class="col-md-4">Product Description </label>  
            <textarea class="form-control" rows = 7 cols = "5"  
            formControlName="ProductDescription"   
            #ProductDescription [(ngModel)] = "product.ProductDescription"></textarea>  
          </div>  
          <div *ngIf="angForm.controls['ProductDescription'].invalid && (angForm.controls['ProductDescription'].dirty || angForm.controls['ProductDescription'].touched)" class="alert alert-danger">  
            <div *ngIf="angForm.controls['ProductDescription'].errors.required">  
              Product Description is required.  
            </div>  
          </div>  
          <div class="form-group">  
            <label class="col-md-4">Product Price</label>  
            <input type="text" class="form-control"   
              formControlName="ProductPrice"   
              #ProductPrice  
              [(ngModel)] = "product.ProductPrice"  
            />  
          </div>  
          <div *ngIf="angForm.controls['ProductPrice'].invalid && (angForm.controls['ProductPrice'].dirty || angForm.controls['ProductPrice'].touched)" class="alert alert-danger">  
            <div *ngIf="angForm.controls['ProductPrice'].errors.required">  
              Product Price is required.  
            </div>  
          </div>  
          <div class="form-group">  
            <button (click) = "updateProduct(ProductName.value, ProductDescription.value, ProductPrice.value)" type="submit" class="btn btn-primary"  
            [disabled]="angForm.invalid" >  
              Update Product  
            </button>  
          </div>  
        </form>  
      </div>  
    </div>  

---------------------------------------------------------------------------------------------
# products.service.ts

Now, use the following code to update the data inside the products.service.ts file, we need to write the function that updates the data.

    updateProduct(ProductName, ProductDescription, ProductPrice, id) {  
        const obj = {  
          ProductName,  
          ProductDescription,  
          ProductPrice  
        };  
        this  
          .http  
          .post(`${this.uri}/update/${id}`, obj)  
          .subscribe(res => console.log('Done'));  
    }  
	
---------------------------------------------------------------------------------------------
# product-edit.component.ts

Now, write the updateProduct() function inside product-edit.component.ts file.

    updateProduct(ProductName, ProductDescription, ProductPrice, id) {  
        this.route.params.subscribe(params => {  
          this.ps.updateProduct(ProductName, ProductDescription, ProductPrice, params.id);  
          this.router.navigate(['products']);  
        });  
      }  

Let's check the edit functionality. In the above read operation, we have seen that there are two duplicate entries of Radio like this: 

Now, we will change the second entry of Radio with Stereo. 

---------------------------------------------------------------------------------------------
# Delete the Data

# product-get.component.html

This is the last step of CRUD operation. We have successfully deployed CREATE, READ, and UPDATE operation till now.

So, to make the DELETE operation possible, we have to define a click event on the delete button inside the product-get.component.html file.

    <tbody>  
          <tr *ngFor="let product of products">  
              <td>{{ product.ProductName }}</td>  
              <td>{{ product.ProductDescription }}</td>  
              <td>{{ product.ProductPrice }}</td>  
              <td><a [routerLink]="['/edit', product._id]" class="btn btn-primary">Edit</a></td>  
              <td><a (click) = "deleteProduct(product._id)" class="btn btn-danger">Delete</a></td>
          </tr>  
      </tbody> 
---------------------------------------------------------------------------------------------
# product-get.component.ts

Now, we have to write a deleteProduct() function inside the product-get.component.ts file.

    deleteProduct(id) {  
        this.ps.deleteProduct(id).subscribe(res => {  
          this.products.splice(id, 1);  
        });  
    }
		
---------------------------------------------------------------------------------------------
# product.service.ts

At last, create deleteProduct() function inside the product.service.ts file.

    deleteProduct(id) {  
        return this  
                  .http  
                  .get(`${this.uri}/delete/${id}`);  
      }  

DELETE operation is completed now. Let's check how it is working. Here, we delete the second item Stereo which we have edited first. 
---------------------------------------------------------------------------------------------

You can see that Stereo is deleted now. You can also verify it on MongoDB Compass Community GUI.
 
---------------------------------------------------------------------------------------------
# Reference link : https://www.javatpoint.com/angular-8
---------------------------------------------------------------------------------------------
