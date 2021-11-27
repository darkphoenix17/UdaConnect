FROM python:3.7-alpine

WORKDIR .

RUN apk add --no-cache gcc musl-dev linux-headers build-base libc-dev
COPY requirements.txt requirements.txt

RUN python -m pip install --upgrade pip
RUN python -m pip install --upgrade setuptools
RUN pip install -r requirements.txt

COPY . .
RUN python -m grpc_tools.protoc -I./ --python_out=./ --grpc_python_out=./ location.proto

EXPOSE 5005

CMD ["python","./main.py"] 