FROM python:3.8-alpine


WORKDIR /app/backend

COPY requirements.txt /app/backend/

# Build psycopg2-binary from source -- add required required dependencies

RUN apk add --virtual .build-deps --no-cache postgresql-dev gcc python3-dev musl-dev && \
        pip install --no-cache-dir -r requirements.txt && \
        apk --purge del .build-deps
RUN apk --no-cache add curl

COPY entrypoint.sh /app/backend/
COPY . /app/backend/
ENTRYPOINT ["entrypoint.sh" ]
CMD [ "python", "manage.py", "runserver", "0.0.0.0:8000" ]