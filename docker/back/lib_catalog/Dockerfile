FROM python:3.7

WORKDIR /backend

COPY . .

RUN pip install --upgrade pip && pip install -r requirements.txt

EXPOSE 8000

ENTRYPOINT ["python", "manage.py", "runserver", "0.0.0.0:8000"]