# -------- Stage 1: Builder --------
FROM python:3.10-slim AS builder

WORKDIR /app

# Install Flask directly in a custom directory
RUN pip install --upgrade pip && \
    pip install --prefix=/install Flask==2.3.3

# Copy app
COPY app.py .

# -------- Stage 2: Runtime --------
FROM python:3.10-slim AS runner

WORKDIR /app

# Copy installed dependencies
COPY --from=builder /install /usr/local

# Copy the app code
COPY --from=builder /app/app.py .

EXPOSE 8002

CMD ["python", "app.py"]
