Docker Images and Containers

Docker Images

Definition: Templates used to create containers.

Purpose: They contain everything needed to run an application — code, libraries, dependencies, and environment settings.

Analogy: If a container is a dish, an image is the recipe.

Docker Containers

Definition: Running instances of Docker images.

Purpose: Containers are what you actually interact with — they execute the application inside an isolated environment.

Key Feature: Containers are ephemeral; changes made in a container do not affect the original image unless explicitly committed.

Dockerfile

Definition: A text file containing a set of instructions to build a Docker image.

Purpose: Defines exactly how an image should be constructed, including:

Base image

Application code

Dependencies

Environment variables

Commands to run

Analogy: If an image is a recipe, the Dockerfile is the step-by-step instructions for writing that recipe.
