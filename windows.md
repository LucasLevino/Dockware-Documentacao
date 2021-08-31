
### I**nstalação**

1. Crie um arquivo `docker-compose.yml`

    ```yaml
    version: '3'

    services:
    	***nome_container***:
    		container_name: ***nome_container***
    		image: dockware/dev:latest
    		ports:
    		- "22:22" # ssh
    		- "80:80" # apache2
    		- "443:443" # apache2 https
    		- "8888:8888" # watch admin
    		- "9998:9998" # watch storefront proxy
    		- "9999:9999" # watch storefront
    		- "3306:3306" # mysql port

    networks:
    	- web
    environment:
    	- XDEBUG_ENABLED=0
    ## ***********************************************************************
    ## NETWORKS
    ## ***********************************************************************
    networks:
    	web:
    		external: false 
    ```

    1. na Pasta abra o CMD e execute 

    ```powershell
    docker-compose up -d
    ```

    3.Por limitações do windows em relação a caminho com nomes compridos vá no 

    **CMD - Como a*dmin**  dentro da pasta*

    ```powershell
    docker exec -it ***nome_container*** zip -r dockware.zip ./
    ```

    ```powershell
    docker cp shopware:/var/www/html/dockware.zip ***CAMINHO_DA_PASTA***\dockware.zip
    ```

    1. Extraia o arquivo na pasta
    2. Clone [https://github.com/shopware/platform](https://github.com/shopware/platform) como .zip e extraia o arquivo na pasta, se precisar edite o nome da pasta para que seja **platform**
