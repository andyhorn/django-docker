# pull the Python Alpine base image
FROM python:3.8.0-alpine

# Set the working directory
WORKDIR /usr/src/app

# Set Python environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Install PostgreSQL dependencies (psycopg2)
RUN apk update \
	&& apk add postgresql-dev gcc python3-dev musl-dev

# Install dependencies
RUN pip install --upgrade pip
COPY ./requirements.txt /usr/src/app/requirements.txt
RUN pip install -r requirements.txt

# Copy the entry point script
COPY ./entrypoint.sh /usr/src/app/entrypoint.sh

# Copy the project files
COPY . /usr/src/app

# Run the entry point script
ENTRYPOINT ["/usr/src/app/entrypoint.sh"]
