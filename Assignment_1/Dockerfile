FROM python:3.11-slim

# Системные зависимости для torchaudio (ffmpeg, libsndfile)
RUN apt-get update && apt-get install -y --no-install-recommends \
    ffmpeg \
    libsndfile1 \
    libsndfile1-dev \
    sox \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Устанавливаем PyTorch CPU + torchaudio + jupyter
RUN pip install --no-cache-dir \
    torch==2.3.1 \
    torchaudio==2.3.1 \
    --index-url https://download.pytorch.org/whl/cpu

RUN pip install --no-cache-dir \
    jupyter \
    notebook \
    matplotlib \
    numpy \
    soundfile

# Порт Jupyter
EXPOSE 8888

# Запуск Jupyter без аутентификации
CMD ["jupyter", "notebook", \
     "--ip=0.0.0.0", \
     "--port=8888", \
     "--no-browser", \
     "--allow-root", \
     "--NotebookApp.token=''", \
     "--NotebookApp.password=''"]