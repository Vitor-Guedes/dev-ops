# DEVOPS
Pequeno projeto para aprender  um pouco de gerenciamento de recursos dev-ops

## Evolução do estudo

#### Imagem e container
Criação do container PHP Apache com código bem simples
```bash
docker build -t app-php .
```

Execução da imagem com variavel de ambiente para poder identificar
```bash
docker run -p 80:80 -e APP_ID="app-php-01" -d --name php-app php-app
```

#### Docker Composer e Nginx
Criação de uma estrutura onde o Nginx vai realizar o load balance e distribuir as requisições para os container php-apache.
Usando as mesmas imagens e códigos da entapa anterior.
```bash
docker compose up -d
```