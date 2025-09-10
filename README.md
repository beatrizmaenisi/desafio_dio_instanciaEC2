# Gerenciando instâncias EC2 na AWS

## Conceitos fundamentais

### EC2 (Elastic Compute Cloud)
É um serviço da Amazon que fornece a capacidade de computação escalável na nuvem do AWS através de máquinas virtuais, conhecidas como instâncias.
### EBS (Elastic Block Store)
É uma storage altamente confiável que pode ser anexado em qualquer instância EC2. Toda instância possui um volume de armazenamento. 
### S3 (Simple Storage Service)
É um serviço de armazenamento de objetos em nuvem oferecidos pela AWS. É ideal para armazenar, organizar e recuperar grandes volumes de dados de forma segura e escalável. 
### RDS (Relational Database Service)
É um banco de dados relacional gerenciado pela AWS. Ou seja, organiza dados em tabelas, colunas e linhas. 
### Lambda
É um serviço de computação serverless da AWS. Ao escrever um código (Python, Node.js, .NET, etc), a AWS executa apenas quando necessário, não precisa configurar o servidor, a AWS escala automaticamente. 
### Dynamo
É um banco de dados NoSQL gerenciado pela AWS. Diferente do RDS, ele armazena dados em chave-valor. 


## Diagramas de arquiteturas
<img width="661" height="533" alt="Image" src="https://github.com/user-attachments/assets/d15e31f2-bfed-4f41-bbf7-1cc0535cd016" /><br>  
O diagrama acima representa uma arquitetura baseada em servidores EC2.  
1. Actor (usuário) envia um arquivo para a infraestrutura AWS
2. O arquivo vai para a instância EC2 (um servidor virtual dentro da AWS).
3. Essa EC2 está conectada a volumes EBS:
- D - EBS: pode ser usado para entrada de arquivos (armazenar temporariamente ou para processamento).
- E - EBS: pode ser usado para saída, backups ou resultados processados.
4. A instância EC2 também pode se comunicar com um RDS
<br>

<img width="657" height="262" alt="Image" src="https://github.com/user-attachments/assets/c3da1418-6ec5-4f3e-ad41-63bafd053049" /><br>
O diagrama acima representa uma arquitetura usando S3 e Lambda.
1. O sistema de arquivos (usuário) envia o arquivo diretamente para o S3 (armazenamento de objetos da AWS).
- Isso pode ser feito via AWS CLI, SDKs ou API.
2. Quando o arquivo chega no S3, ele dispara um Trigger.
3. Esse trigger ativa uma função Lambda, que pode ser escrita em Node.js, .NET Core ou Python.
4. O resultado ou metadados são gravados em um DynamoDB. 
