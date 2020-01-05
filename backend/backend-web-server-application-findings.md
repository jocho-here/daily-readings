# Backend components

## Before Today's findings
- I thought Flask is THE backend server that deals with API as well as incoming requests
- I never really thought of multiple requests coming in at once being a problem until I worked on WhoAmI project and faced concurrent requests being a problem
- I also heard of these Gunicorn, Nginx, Apache, etc.  Knew that Nginx and Apache were load balancers but didn't really know the separation between all those

## After Today's findings
- Nginx and Apache are at the most front side of backend, dealing directly with user requests.  The main use of those load balancers is to balance out requests to running servers.
- WSGI (Web Server Gateway Interface) is Python specification of what load balancers do.  There are web application frameworks/ libraries that implemented using WSGI protocol, such as Werkzeug, which Flask is a wrapper of.
- ASGI stands for Asynchronous Server Gateway Interface, which is async version of WSGI.
- Uvicorn uses ASGI specification for interacting with an application.  It runs asynchronous Pytho nweb code in a single process.
- Gunicorn is a Python WSGI HTTP server for UNIX.  If used with Uvicorn, it manages Uvicorn and runs multiple of these concurrent processes for concurrency and parallelism.
- Starlette is a ASGI framework/ toolkit.  FastAPI depends on (wraps) Starlette, just like Flask depending on (wrapping) Werkzeug.
- So for a consistent and strong web server, I need
1. Nginx/ Gunicorn/ Apache/ uWSGI as WSGI Container (+ Uvicorn if you want a ASGI container)
2. Flask/ Django/ Pyramid as WSGI web application (or FastAPI/ Starlette/ Tornado for ASGI web application).

## Reference
- https://github.com/tiangolo/uvicorn-gunicorn-fastapi-docker
    - Uvicorn, Gunicorn, and FastAPI combination