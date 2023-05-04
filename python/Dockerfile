
# python version number:3.9.16
FROM python:3.9.16

# code ... directory for python codes.
WORKDIR /code

# copy localcode to container image.
COPY ./code /code


RUN pip install --upgrade pip 

RUN pip install -r requirements.txt

# CMD ["python", "index.py"]
