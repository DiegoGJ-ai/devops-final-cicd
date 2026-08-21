# Práctica Final DevOps CI/CD con GitHub Actions

Aplicación web "Hola Mundo" desarrollada con Python y Flask. El proyecto implementa integración y despliegue continuo utilizando GitHub Actions, Docker Hub y Render.

## Requisitos implementados

- Repositorio Git con aplicación web.
- Pruebas unitarias con pytest.
- Dockerfile para contenerizar la aplicación.
- Pipeline de GitHub Actions que:
  - instala las dependencias;
  - ejecuta las pruebas unitarias;
  - construye la imagen Docker;
  - publica la imagen en Docker Hub;
  - activa el despliegue de producción en Render.

## Estructura

```text
.
├── .github/
│   └── workflows/
│       └── ci-cd.yml
├── templates/
│   └── index.html
├── tests/
│   └── test_app.py
├── app.py
├── Dockerfile
├── requirements.txt
├── .dockerignore
├── .gitignore
└── README.md
```

## Ejecutar localmente

```bash
python -m venv venv
```

Windows:

```bash
venv\Scripts\activate
```

Instalar dependencias:

```bash
pip install -r requirements.txt
```

Ejecutar pruebas:

```bash
pytest -v
```

Ejecutar la aplicación:

```bash
python app.py
```

Abrir:

```text
http://localhost:10000
```

## Ejecutar con Docker

```bash
docker build -t devops-final-cicd .
docker run -p 10000:10000 devops-final-cicd
```

## Secrets necesarios en GitHub

En:

`Settings > Secrets and variables > Actions > New repository secret`

Crear:

- `DOCKER_USERNAME`: usuario de Docker Hub.
- `DOCKER_TOKEN`: Personal Access Token de Docker Hub.
- `RENDER_DEPLOY_HOOK_URL`: Deploy Hook secreto del servicio creado en Render.

## Docker Hub

Crear un repositorio público llamado:

`devops-final-cicd`

La imagen utilizada por Render será:

`docker.io/TU_USUARIO_DOCKER/devops-final-cicd:latest`

## Render

> En el primer push puedes configurar solamente `DOCKER_USERNAME` y `DOCKER_TOKEN`.
> El workflow subirá la imagen a Docker Hub y omitirá temporalmente el paso de Render.

Cuando la imagen ya exista en Docker Hub, crear un **Web Service** usando **Existing Image** y colocar:

`docker.io/TU_USUARIO_DOCKER/devops-final-cicd:latest`

Después de crear el servicio:

1. Abrir `Settings`.
2. Buscar `Deploy Hook`.
3. Copiar la URL.
4. Guardarla en GitHub como el secret `RENDER_DEPLOY_HOOK_URL`.
5. Hacer otro commit/push a `main` para ejecutar el pipeline completo.

## Evidencia final

Después de hacer un `git push` a `main`, en la pestaña **Actions** de GitHub deben aparecer en verde:

1. Instalar dependencias
2. Ejecutar pruebas unitarias
3. Iniciar sesión en Docker Hub
4. Construir y subir imagen a Docker Hub
5. Publicar nueva versión en Render

## Enlaces para entregar

Repositorio público:

`https://github.com/DiegoGJ-ai/devops-final-cicd`

Aplicación desplegada:

`https://devops-final-cicd-7xpc.onrender.com/`
