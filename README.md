# nacfiap
Repositório para execução da NAC do 2ºTRCR

Para a conclusão do projeto tanto o apache server quanto o mediawiki foram instalados por automação via Ansible com base no repositório Git: https://github.com/fiapsistemaslinux/iac/tree/master/ansible
Obs: Lab utilizando uma instância EC2 da AWS

Feito isso temos a seguinte missão:
- Instalar o banco;
- Criar a base de dados;
- Criar um usuário de acesso ao banco;
- Criar um virtualhost para o mediawiki;

Vamos nessa:
Geramos uma chave pública e outra privada para que o ansible consiga acessar via ssh nossa máquina para completar nossas missões dadas acima.
 
![1](https://user-images.githubusercontent.com/51094112/67945598-123f3100-fbbe-11e9-8b46-2884dbfe5a25.png)

Após a geração da chave adicionamos ela no authorized_keys para acesso remoto em nosso server.
 
![2](https://user-images.githubusercontent.com/51094112/67945644-2f73ff80-fbbe-11e9-87aa-2ae02f956250.png)

Após isso instalamos o ansible conforme o link: https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html
 
![3](https://user-images.githubusercontent.com/51094112/67945651-31d65980-fbbe-11e9-9455-9b7bbec55f01.png)

Realizado o git clone do repositório GIt https://github.com/fiapsistemaslinux/iac
 
![4](https://user-images.githubusercontent.com/51094112/67945657-3995fe00-fbbe-11e9-966e-d4e612a3dae9.png)

Feito isso, iremos adicionar o nosso ip no arquivo de inventário e logos após realizamos um teste de ping para ver se está tudo ok:

![5](https://user-images.githubusercontent.com/51094112/67945662-3c90ee80-fbbe-11e9-87a2-1210d1b44e41.png)

Essa se trata da nossa role para instalação dos pacotes do mediawiki, o apache server e nosso banco.

![6](https://user-images.githubusercontent.com/51094112/67945666-3f8bdf00-fbbe-11e9-8b9f-ddb3eca930db.png)
 
Agora será realizada a criação da task para instalação do banco mariadb. Para isso criamos o diretório dentro de roles “mysql” e dentro dele o diretório “tasks” contendo o arquivo main.yml.

![7](https://user-images.githubusercontent.com/51094112/67945677-44509300-fbbe-11e9-8164-be5b0d9c01cb.png)

![8](https://user-images.githubusercontent.com/51094112/67945684-47e41a00-fbbe-11e9-9d51-d437c1add99c.png)
 
Feito isso, realizaremos a instalação do nosso mediawiki, apache server e banco de dados.

![9](https://user-images.githubusercontent.com/51094112/67945692-4ca8ce00-fbbe-11e9-85a1-85a18b5b0113.png)
 
Com isso, a instalação do banco está feita e o mediawiki funcionando para acesso.

![10](https://user-images.githubusercontent.com/51094112/67945697-52061880-fbbe-11e9-849c-dd3b1559cf5e.png)

![11](https://user-images.githubusercontent.com/51094112/67945705-56cacc80-fbbe-11e9-98c7-68e02c3a530c.png) 

![12](https://user-images.githubusercontent.com/51094112/67945711-59c5bd00-fbbe-11e9-9f34-ff6e81eb79c9.png)

Agora criaremos a role database para criação do banco de dados e do usuário do banco
 
![13](https://user-images.githubusercontent.com/51094112/67945717-5cc0ad80-fbbe-11e9-8b93-71ccfcf52bb0.png)


Criado o diretório “banco” e dentro dele “task” contendo o arquivo main.yml

![14](https://user-images.githubusercontent.com/51094112/67945726-634f2500-fbbe-11e9-81b0-60aff34b18df.png)

![15](https://user-images.githubusercontent.com/51094112/67945733-677b4280-fbbe-11e9-8d5d-e9a25af300e7.png)

 
Realizada a instalação do zabbix conforme o link:

https://www.zabbix.com/download?zabbix=4.0&os_distribution=ubuntu&os_version=18.04_bionic&db=mysql

![zabbix_1](https://user-images.githubusercontent.com/51094112/67946269-becde280-fbbf-11e9-8600-1b4887e14d2b.PNG)

![zabbix_2](https://user-images.githubusercontent.com/51094112/67946274-c3929680-fbbf-11e9-8a66-27ba39ee7792.PNG)

![zabbix_3](https://user-images.githubusercontent.com/51094112/67946278-c5f4f080-fbbf-11e9-8962-8d25f80eacc3.PNG)

Feita instalação, as configurações no arquivo zabbix_agentd.conf foram setadas

![zabbix_4](https://user-images.githubusercontent.com/51094112/67946286-cc836800-fbbf-11e9-8221-7c1f24dab420.PNG)

![zabbix_5](https://user-images.githubusercontent.com/51094112/67946293-cf7e5880-fbbf-11e9-8dca-8c80105f0945.PNG)

Realizada as configurações no arquivo zabbix_agentd.d/userparameter_mysql.conf

![zabbix_6](https://user-images.githubusercontent.com/51094112/67946296-d311df80-fbbf-11e9-845f-a0e553b6597a.PNG)

Criado o arquivo de monitoramento do banco mysql e do zabbix

![zabbix_7](https://user-images.githubusercontent.com/51094112/67946302-d6a56680-fbbf-11e9-8486-ce2ace25d94b.PNG)

Selecionado o Template Mysql

![zabbix_8](https://user-images.githubusercontent.com/51094112/67946308-d9a05700-fbbf-11e9-9530-ffcee02c225c.PNG)

![zabbix_9](https://user-images.githubusercontent.com/51094112/67946318-de650b00-fbbf-11e9-8f43-4840004be104.PNG)
