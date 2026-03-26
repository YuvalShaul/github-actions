## Python Workflow

Create a **python workflow** demo.


### Components

- A new private github repository
- A python file - basic flask example  -   saved in git
- A requirements.txt file (with a list of what needs to be installed - flask)
- A Dockerfile


### What do do
- Changes are done in branches called feature-<num>  (e.g: feature-1  feature-2 ...)
- a single main branch
- Write a workflow:
  - push to feature-x causes a build of an image and push the image to dockerhub
     (keep dockerhub login credentials in your code - private repo for now)
  - don't deal with secrets yet
  - push to main (actually merging a pull-request but GA will trigger "push" event) causes to creating an image, pushing it to dockerhub but also running a "curl" test on the runner.