# Desafio-pipeline-utilizando-Gitlab-dockers-e-Kubernets

Estrutura do Repositório
Crie o Repositório:

Nome: docker-microservices-project
Descrição: "Projeto de microserviços utilizando Docker para gerenciar aplicações e serviços de forma eficiente."
Estrutura de Pastas:

Copiar código
docker-microservices-project/
├── docker-compose.yml
├── Dockerfile
├── service1/
│   ├── Dockerfile
│   ├── app.py
│   └── requirements.txt
├── service2/
│   ├── Dockerfile
│   ├── app.py
│   └── requirements.txt
├── README.md
└── LICENSE
Exemplo de Conteúdo
1. docker-compose.yml
yaml
Copiar código
version: '3.8'
services:
  service1:
    build:
      context: ./service1
    ports:
      - "5001:5000"
  
  service2:
    build:
      context: ./service2
    ports:
      - "5002:5000"
2. Dockerfile em service1/
dockerfile
Copiar código
# Use uma imagem base do Python
FROM python:3.9

# Defina o diretório de trabalho
WORKDIR /app

# Copie os requisitos e instale as dependências
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copie o restante do código
COPY . .

# Comando para executar a aplicação
CMD ["python", "app.py"]
3. app.py em service1/
python
Copiar código
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "Hello from Service 1!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
4. requirements.txt em service1/
makefile
Copiar código
Flask==2.0.1
5. README.md
markdown
Copiar código
# Projeto de Microserviços com Docker

Este projeto demonstra como usar Docker para gerenciar aplicações de microserviços. Ele contém dois serviços simples construídos com Flask.

## Estrutura do Projeto

- **service1**: Um serviço que retorna uma mensagem de "Hello from Service 1!".
- **service2**: Um serviço que retorna uma mensagem de "Hello from Service 2!" (você pode criar um similar ao serviço 1).

## Instruções para Execução

1. Certifique-se de ter o Docker e o Docker Compose instalados em sua máquina.
2. Clone este repositório.
3. Navegue até o diretório do projeto:
   ```bash
   cd docker-microservices-project
Execute o Docker Compose:
bash
Copiar código
docker-compose up --build
Acesse os serviços nos seguintes endereços:
Service 1: http://localhost:5001
Service 2: http://localhost:5002
