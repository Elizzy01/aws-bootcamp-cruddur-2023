FROM python:3.10-slim-buster

#Inside Container
#Make a new folder inside the container
WORKDIR /backend-flask

#Outside Container ==> Inside container
#this contains the libraries we want to install to run the app
COPY requirements.txt requirements.txt

#Inside the container
#Install the python libraries used for the app
RUN pip3 install -r requirements.txt

#Outside Container --> Inside container
#. means evrything in the current directory
#first . - /backend-flask outside the container
#second . - /backend-flask inside the container
COPY . .

#Set environment variables (Env Vars)
#Inside Container and will remain set when the container is running. 
ENV FLASK_ENV=development

EXPOSE ${PORT}

# CMD -Command
# python3 -m flask run --host=0.0.0.0 --port=4567
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]