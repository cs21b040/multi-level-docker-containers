FROM ubuntu AS build

RUN apt-get update && apt-get install -y golang-go

ENV GO111MODULE=off

COPY . .

RUN CGO_ENABLED=0 go build -o /app .

############################################
# Second stage with a distro less OS for GO#
############################################

FROM scratch

COPY --from=build /app /app
ENTRYPOINT ["/app"]
