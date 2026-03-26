## Python Workflow

Create a **python workflow** demo.


### Components

- Create a new private github repository.
- Create a new python file - basic flask application
- Create a requirements.txt file (with a list of what needs to be installed - e.g flask)
- Create a Dockerfile that creates a python image to run your app.
- Add these files to your repository


### What do do
- Configure branch protection rule to forbid push to your main branch.
- Changes to the repository are to be done in branches called feature-<num>  (e.g: feature-1  feature-2 ...)
- Write a workflow:
  - push to feature-x causes:
    - create the docker image
    - push the image to dockerhub
     (keep dockerhub login credentials in your code - private repo for now)
    - don't deal with secrets yet
  - push to main (actually merging a pull-request but GA will trigger "push" event) causes:
    - create the docker image
    - push the image to dockerhub
    - Run a local container inside the runner.
    - run a local "curl" test inside the runner.
    (make sure that the image returns the correct answer)