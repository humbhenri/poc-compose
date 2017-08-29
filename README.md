# poc-compose
Executa a aplicação inteira via containers docker.
## Dependências
- git
- maven
- jdk8
- docker e docker-compose
## Modo de uso
Em uma pasta limpa, baixar todos os módulos e executar `mvn clean package -Pdocker`. O seguinte script pode ser usado para facilitar.
```
for repo in poc-models poc-cursos poc-apigateway poc-integracao poc-matricula poc-compose poc-service-discovery plataforma-legada-ws poc-db
do
	git clone "https://github.com/humbhenri/$repo.git"
done

for project in poc-models poc-cursos poc-apigateway poc-integracao poc-matricula poc-service-discovery plataforma-legada-ws
do 
	cd "$project"
	mvn clean package install -Pdocker
	cd ..
done

cd poc-compose
docker-compose build
docker-compose up -d
cd ..


```
Acessar a aplicação no [localhost](http://localhost).
