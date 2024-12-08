# iac-start README
Este repositório contém os arquivos necessários para configurar e executar um ambiente de Infraestrutura como Código (IaC) utilizando Terraform dentro de um container Docker. O objetivo é provisionar uma instância na AWS usando o Terraform e posteriormente destruí-la.

## Pré-requisitos
- Docker instalado na sua máquina.
- Credenciais da AWS (Access Key e Secret Key).

## Passo a Passo

### 1. Construir a Imagem Docker
Primeiro, navegue até a pasta onde o Dockerfile está localizado. Em seguida, execute o comando abaixo para construir a imagem Docker:


```
docker build -t iac-start-image:iac .
```

### 2. Executar o Container Docker
Após a construção da imagem, cire o container Docker com o comando abaixo:


```

docker run -dit --name iac-start iac-start-image:iac /bin/bash
```


### 3. Acessar o Terminal do Container
Agora, entre no terminal do container iac-start com o seguinte comando:


```

docker exec -it iac-start /bin/bash
```

### 4. Configurar AWS CLI
Dentro do terminal do container, configure as credenciais da AWS executando o comando:


```

aws configure
```

Digite as credenciais de acesso (Access Key e Secret Key) quando solicitado.

### 5. Inicializar o Terraform
No terminal do container, navegue até o diretório onde o arquivo main.tf está localizado:


```

cd /iac-start
```

Em seguida, execute o comando para inicializar o Terraform:


```

terraform init
```


### 6. Validar o Plano do Terraform
Para validar a configuração e ver o que será provisionado, execute:


```
terraform plan
```

O Terraform mostrará um plano detalhado dos recursos que serão criados na AWS.

### 7. Provisionar a Instância na AWS
Se o plano estiver correto e você estiver pronto para provisionar a instância, execute:


```
terraform apply
```
Isso criará a instância na AWS.

### 8. Destruir os Recursos Provisionados
Após finalizar o uso da instância, você pode destruir a instância EC2 criada:


```
terraform destroy
```
