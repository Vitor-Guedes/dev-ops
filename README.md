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

#### Kubernets + minikube
Para simular um ambiente para devops, instalei o kubernets e minikube localmente. Criar os arquivos kube/*-deployment.
Para usar a imagem anterior da aplicação php-apache eu iniciei o minikube com o comando
```bash
minikube start --driver=docker
```

Depois executei o comando para realizar o deployment do kubernets:
```bash
kubectl create -f kube/deploy
```

#### CICD - Github actions
Após configurar o Github self-hosted, bastou replicar os comandos acima no arquivo .github/workflows/deploy.yml e excutar o runner para poder implatar as atualizações feitas na branch master.


## Objetivos
- Criar uma estrutura de front-end e de backend com repositórios distintos, que vai atualizar as imagens localmente. Ajustar esse projeto para atualizar apenas o devops das aplicações envolvidas. Aproveitar o mesmo runner para atualizar imagens e para fazer o rollout das aplicações.
- Deixar mais dinamico o que se deve atualizr por exemplo, em caso de novas aplicações e serviços fazer com que seja executado o kubectl apply ou create. Se apenas o código foi atualizado executar o rollout