FROM python:3.10-slim
RUN groupadd -r appgroup && \
    useradd -r -g appgroup -m appuser
WORKDIR /app
COPY requirements.txt .
RUN pip install --upgrade pip &&\
    pip install gunicorn==20.1.0 && \
    pip install -r requirements.txt --no-cache-dir
COPY . .
EXPOSE 8000
USER appuser
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "kittygram_backend.wsgi"]

