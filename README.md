## Java project which can be deployed on Heroku

### local project location

- [servlet1](http://localhost:5000/hello)
- [servlet2a](http://localhost:5000/student)
- [servlet2b](http://localhost:5000/student?x=1)

### heroku instruction (steps)

- install heroku cli
- create and upload ssh keys
- check whether everything is ok (locally): `mvn clean install && heroku local web`
- run `heroku login`
- run `heroku create`, should look like this: 
```
Creating app... done, ⬢ young-garden-08016
https://young-garden-08016.herokuapp.com/ | https://git.heroku.com/young-garden-08016.git
```
- look for the git remotes: `git remote -v`, should look like this:
```
heroku  https://git.heroku.com/young-garden-08016.git (fetch)
heroku  https://git.heroku.com/young-garden-08016.git (push)
origin  https://github.com/alexr007/java-heroku.git (fetch)
origin  https://github.com/alexr007/java-heroku.git (push)
```
- push your code to heroku `git push heroku master`

### adding heroku database:
- goto heroku dashboard
- click `your app name`
- click `Resources` 
- in the add-ons type: `Postgres`
- click `Heroku Postgres`
- click `Provision`
- click `Heroku Postgres` in the list below
- goto `Settings`, look for `Credentials` 

#### useful heroku command:

- heroku ps
- heroku open
- heroku ps:scale web=1
- heroku logs --tail

#### Pay your attention to

- `Procfile` contents:
  - fully qualified path to the `main class`
  - `classpath` declaration
- `pom.xml` sections:
  - `<packaging>jar`
  - `<pluginns>maven-dependency-plugin...`

#### note: be aware of  Heroku env variables:

- `DATABASE_URL` looks like `postgres:...`  
- `JDBC_DATABASE_URL` looks like `jdbc:postgresql:...`
- `PORT` http port to listen

### Links

- Heroku official documentation in general: [here](https://devcenter.heroku.com/articles/getting-started-with-java)
- Heroku official documentation about JDBC connection: [here](https://devcenter.heroku.com/articles/connecting-to-relational-databases-on-heroku-with-java)
- Heroku official github code: [here](https://github.com/heroku/java-getting-started)
- Baeldung link how to create runnable `jar` file: [here](https://www.baeldung.com/executable-jar-with-maven)
