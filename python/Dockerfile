FROM ubuntu AS build

RUN apt-get update && apt-get install -y python3 python3-pip

WORKDIR /app

# COPY requirements.txt .

# RUN pip3 install -r requirements.txt

COPY . .

RUN python3 build -o /app .

###############################################
# Second stage with a distro less OS for Pthon#
###############################################

FROM gcr.io/distroless/python3

COPY --from=build /app /app
ENTRYPOINT ["/app"]
