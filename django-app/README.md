# Project Setup

Clone the repository:
   ```bash
   git clone <repo-url>
   cd <repo-name>

## Run App locally

1. Create virtual environment as venv
   python3 -m venv venv

2. Activate the virtual environment and install dependencies:
   source venv/bin/activate
   pip install -r requirements.txt

3. Run the project
   python manage.py runserver

4. Access the app with given link in console

## Create docker image and run the container

1. Build the immage
   docker build -t <image_tag> .

2. Run the image with port mapping. Since we specified 8000 port in Dockerfile, map any available host posrt to container port
   docker run -p <host_port>:<container_port> image

3. Access the app http://localhost:<mapped_host_port> in yout web browser
