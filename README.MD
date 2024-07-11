Projetinho de Django.

# Instalação e preparo do ambiente

### 1 - Criação de um ambiente virtual (Linux)

```bash
python -m venv <nome_do_ambiente>
```
Um nome comum para o ambiente virtual é `.venv`.

Esse comando criará uma pasta com o nome do seu ambiente. É importante colocar essa pasta no `.gitignore` do projeto.

### 2 - Criação de um Arquivo .gitignore

Arquivos `.gitignore` têm por função evitar que informações indesejadas sejam subidas para o repositório do projeto, como chaves de segurança, chaves de API, arquivos muito grandes (como a pasta `node_modules` em projetos em NodeJS) e, no nosso caso, a pasta `.venv` que irá conter todas as bibliotecas utilizadas no nosso projeto.

Exemplo de um `.gitignore` básico:
```gitignore
# Ignore virtual environment folder
.venv/

# Ignore Python cache files
__pycache__/
*.py[cod]
```

### 3 - Criar o arquivo `requirements.txt`

Para que o projeto funcione em outra máquina sem a necessidade de copiar as bibliotecas manualmente, criamos um arquivo `requirements.txt`. O comando para realizar isso é:

```bash
pip freeze > requirements.txt
```

### 4 - Verificar e instalar o Django

Verifique se o Django está instalado:
```bash
python -m django --version
```

Se não estiver instalado, use o seguinte comando para instalar:
```bash
python -m pip install django
```

### 5 - Iniciar o projeto Django

Para começar seu projeto em Django:
```bash
django-admin startproject <nome_do_projeto>
cd <nome_do_projeto>
django-admin startapp <nome_do_app>
```

### 6 - Configurar o ambiente de desenvolvimento

#### Realizar migrações

Para preparar os models para serem salvos no banco de dados, execute:
```bash
python manage.py makemigrations <app>
```
Atenção: Rodando esse comando sem especificar um app, você atualizará todos os models, não apenas os de um app específico.

Para efetivar as alterações no banco de dados, execute:
```bash
python manage.py migrate
```

#### Rodar o servidor de desenvolvimento

Para rodar o projeto Django, por padrão na porta 8000 (localhost:8000):
```bash
python manage.py runserver
```

### Estrutura do Projeto

- `manage.py`: Script de utilidade para interagir com o projeto Django.
- `<nome_do_projeto>/`: Diretório do projeto principal.
  - `__init__.py`: Arquivo para indicar que este diretório deve ser tratado como um pacote Python.
  - `settings.py`: Configurações do projeto.
  - `urls.py`: Rotas do projeto.
  - `wsgi.py`: Configuração para o servidor WSGI.

- `<nome_do_app>/`: Diretório da aplicação específica.
  - `__init__.py`: Arquivo para indicar que este diretório deve ser tratado como um pacote Python.
  - `models.py`: Definição dos modelos de dados.
  - `views.py`: Lógica das views.
  - `urls.py`: Rotas da aplicação.
  - `admin.py`: Configurações do admin.

---
