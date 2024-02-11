FROM python:3-slim AS build
WORKDIR /app
COPY src/* /app/
RUN pip install -r requirements.txt

FROM build as dev
ENTRYPOINT [ "flask", "--app hello run --debug" ]

FROM gcr.io/distroless/python3 as runtime
COPY --from=build-env /app /app
WORKDIR /app
CMD ["hello.py"]
