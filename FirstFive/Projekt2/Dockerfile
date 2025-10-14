FROM python:3.10-slim
WORKDIR /app
COPY . .
RUN pip install --no-cache-dir Flask
EXPOSE 80
ENV PORT 80
ENV VERSION latest
CMD ["python3", "app.py"]
