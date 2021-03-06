# smile-widget-code-challenge

The Smile Widget Company currently sells two types of smile widgets: a Big Widget and a Small Widget.  We'd like to add more flexibility to our product pricing.

## Setup with Docker
1. Install Docker (https://docs.docker.com/install/)
2. Clone this repository.
3. `>>> docker-compose up --build`

## Setup without Docker
1. Install Python (>3.4)
2. Install postgres.  By default the Django app will connect to the database named 'postgres'.  See `settings.DATABASES`.
3. Clone this repository.
4. Install requirements.
  * `>>> pip install -r requirements.txt`
5. Run migrations.
  * `>>> python manage.py migrate`
6. Load data from fixtures:
  * `>>> python manage.py loaddata 0001_fixtures.json`

### Technical Requirements
* We currently have to products with the following prices:
    * Big Widget - $1000
    * Small Widget - $99
* These products, along with existing gift cards are already setup in the database.  Study the existing models and initial data.
* Create a new ProductPrice model and setup the following price schedule:    
  * Black Friday Prices (November 23, 24, & 25)
    * Big Widget - $800
    * Small Widget - FREE!
  * 2019 Prices (starting January 1, 2019)
    * Big Widget - $1200
    * Small Widget - $125
* Build a JSON API endpoint that accepts a product code, date, and (optional) gift card and returns product price.
  * The endpoint should live at `api/get-price` and accept the following parameters:
    * `"productCode"`
    * `"date"`
    * `"giftCardCode"`
* Update this README file with instructions on how to run and access your price calculator.
* Create a pull request with your changes.

### Additional Information
* Please use Django Rest Framework or a Python web framework of your choice to create the endpoint.
* Just as a general guideline, we've designed this exercise to take less than 4 hours.

### Updated by Harish
1. Create database and configure the setting.py file.

2. Open the terminal and run the below commands:
  * `>>> python manage.py makemigrations` # Propagating changes made in the model into the database schema
  * `>>> python manage.py migrate` # updates the database schema
  * `>>> python manage.py loaddata 0002_fixtures.json` # load the data into tables
  * `>>> python manage.py runserver` # run the server
  
3. Check the API (http://127.0.0.1:8000/api/get-price) from any API connector by passing below kind of json data 
  * `{"giftCardCode": "10OFF", "productCode": "big_widget","date": "2018-11-24"}`


