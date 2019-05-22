FROM python:3 as build

WORKDIR /app
COPY requirements.txt main.py ./
RUN pip install -r requirements.txt

# Smallest Size
FROM python:3.7-alpine3.9 as run

COPY --from=build /app /app
EXPOSE 5000
CMD ["main.py"]

# Smallest Attack Surface
FROM gcr.io/distroless/python3 as deploy

COPY --from=build /app /app
EXPOSE 5000
CMD ["main.py"]