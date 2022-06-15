#### Stage 1: Build the flask application
FROM python:3.8-slim

# Configure the main working directory inside the docker image.
# This is the base directory used in any further RUN, COPY, and ENTRYPOINT
# commands.
WORKDIR /app

# If you are building your code for production
# RUN npm ci --only=production

# Copy the main application
COPY . ./

RUN pip install -r requirements.txt

# Expose port 3000 to the Docker host, so we can access it
# from the outside.
EXPOSE 5000

CMD ["python3", "-m", "flask", "run", "--host=0.0.0.0"]