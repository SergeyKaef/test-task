FROM python:3.12-alpine

WORKDIR /app

COPY app.py .

RUN addgroup -S appgroup && adduser -S appuser -G appgroup && \
    chown -R appuser:appgroup /app

USER appuser

EXPOSE 8080

HEALTHCHECK --interval=10s --timeout=3s --start-period=3s --retries=3 \
  CMD pgrep -f "python app.py" || exit 1

CMD ["python", "app.py"]