# build a image for Python AWS Lambda with the lastest version of pandas
FROM public.ecr.aws/lambda/python:3.10

# Install the function's dependencies using file requirements.txt
# from your project folder.
COPY requirements.txt  .
RUN pip install -r requirements.txt


# Copy the main Lambda handler function
COPY app.py  .

# Copy the lib directory if you have one
#COPY lib/ ./lib 

# Set the CMD to your handler (could also be done as a parameter override outside of the Dockerfile)
CMD [ "app.lambda_handler" ]