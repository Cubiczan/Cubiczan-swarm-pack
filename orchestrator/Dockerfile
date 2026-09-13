FROM python:3.12-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

RUN groupadd --system --gid 10001 appuser \
    && useradd --system --uid 10001 --gid 10001 --home-dir /app --no-create-home --shell /usr/sbin/nologin appuser \
    && mkdir -p /app/audit \
    && chown -R 10001:10001 /app

EXPOSE 5002

USER 10001

CMD ["python", "server.py"]
