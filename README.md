# ITK Panoramax Docker [Dev]

ITK docker setup for [Panoramax](https://panoramax.fr/) and [Docs](https://docs.panoramax.fr/)

### IMPORTANT:   
This is a dev setup intended for local testing. It is not suitable for STG/PROD hosting.

## Usage

`docker compose up -d`

This will give you the following setup:

GeoVisio backend, a database, a blurring API and a keycloak for authentication they use the local network in order for 
the oauth dance to work (keycloak should be accessible by the `backend` service and the user's browser)
* Keycloak is accessible through http://localhost:8182
* Backend is accessible through http://localhost:5001
* Blurring API is accessible through http://localhost:5500
* Website is accessible through http://localhost:3000

For both the website and for Keycloak an admin user is created automatically with username: `admin`, password: `password`.
To create additional users you can access the Keycloak Administration Console and select the realm "geovisio".

### Note:
There is an issue with the map view that we have not been able to debug. You may experience a "beige" view on the 
website (http://localhost:3000) while seeing a functioning map on the backend (http://localhost:5001). 

## ITK Dev standard setup and Traefik
A quick test was made to see if trafik labels could be setup to have a panoramax.local.itkdev.dk domain working. But
the various containers gave a "bad gateway" error. We need to look into how the various components need to be configured
behind a proxy to make it work.
