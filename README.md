At Love, Bonito, we are looking for Backend developers that show PHP proficiency using all the good practices. You can use https://phptherightway.com/ for reference. 


### Considerations

- Every piece of code needs to have a unit test. Code coverage needs to be close to 100%
- Every functionality needs to have a functional/integration test. 
- The documentation needs to be precise and tidy. You can use Markdown and save it on the `doc` folder
- Use Docker to spin up the application and docker-compose for all the services need it 
- We pre-install some libraries, but you don't necessarily need to use all of them
- Codeception is an excellent tool for testing, but you can use plain PHPUnit if you feel uncomfortable.




### Context

City information doesn't change often, but anyways to avoid any inconvenience with our Logistics carrier. We update the content as soon we have a chance. 


There are two ways that we can receive the updates of the cities. 



1. As a CSV file with all the cities.
2. As an API request, one request for each city


In the case of the CSV file, we will place it manually in storage/worldcities.csv


We pre-install some libraries to help you out on the initial setup. The use of those libraries is not mandatory. Still, you cannot use any other framework like Laravel or Lumen.

It's essential to understand unit tests and functional tests. Both are being required for the Challenge. We will not consider tests without them. 


### We recommend 
- Use Tactician and follow the Command Bus Pattern
- Testing is crucial for us. Try to solve the Challenges using TDD 





### Challenge 1

Dockerize the application in the simplest way possible. Do not use external services. Just a simple docker-compose.yml will do the job.


**Acceptance Criteria**

- The application should spin up simply doing `docker-compose up -d'
- I should be able to access the API and all the commands using Docker


### Challenge 2 

Whenever the file storage/worldcities.csv changes, we should update accordingly.

We need to detect as soon as possible any change on the worldcities.csv file and save the latest information in storage/cities.csv 

Cities.csv will contain all the updated information but just the Cities from ASEAN countries, Brunei, Cambodia, Indonesia, Laos, Malaysia, Myanmar, The Philippines, Singapore, Thailand, and Vietnam.

**Acceptance Criteria**

- The process shouldn't be executed if the file worldcities.csv doesn't change
- The final will only contain the cities from ASEAN countries
- The process should be as fast as possible
- I should be able to execute the script with one line using docker like 
	`$ docker exec -t {ContainerName} php folder/fileName.php {?params}`



### Challenge 3

Another way to update cities is through the API. We need to make an API endpoint PUT `/cities/{city_id}/` 

This method will get only one city at a time. 

Remember that you will save information in storage/cities.csv

**Acceptance Criteria**

- Lookout to don't overlap the saving of the cities with another request or even with Challenge 1

- A proper test will be run in parallel 1000 updates for different cities and update the worldcities.csv file at the same time, and nothing should overlap


### Delivery of the project

Please share the repository URL with pablo.morales@lovebonito.com and aman.agarwal@lovebonito.com. Remember to let Beverly (beverly.shaddick@lovebonito.com) know that you have finished the Challenge.

 
 


### Other references

- Slim 4 https://www.slimframework.com/docs/v4/
- Codeception https://codeception.com/
- PHP League https://thephpleague.com/
- Tactician https://tactician.thephpleague.com/
- CSV Lib https://csv.thephpleague.com/
- PHP Container https://container.thephpleague.com/
