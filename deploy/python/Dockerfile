FROM python:3.10

ENV PYTHONUNBUFFERED 1

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

EXPOSE 8000

RUN python manage.py collectstatic --noinput

CMD python manage.py migrate && \
	uwsgi deploy/python/uwsgi.ini --static-map /static=/app/static