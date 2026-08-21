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

Repositorio público:

`https://github.com/DiegoGJ-ai/devops-final-cicd`

Aplicación desplegada:

`https://devops-final-cicd-7xpc.onrender.com/`
