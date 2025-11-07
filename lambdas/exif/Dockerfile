FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

WORKDIR /var/task

COPY pyproject.toml ./
RUN uv sync

COPY handler.py ./

ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    PYTHONPATH=/var/task/.venv/lib/python3.13/site-packages:/var/task

CMD ["handler.exif_handler"]