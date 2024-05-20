# Ponderada - Semana 5
## TEMA 1

CI/CD é necessário no desenvolvimento de software moderno, pois automatiza e agiliza o processo de integração e entrega de código. Isso permite que as equipes de desenvolvimento sejam mais eficientes e produtivas, reduzindo o tempo entre a escrita do código e sua implementação em produção. A automação de testes e deploys garante a qualidade do código, minimiza riscos de erros e falhas, e permite feedback rápido, essencial para o desenvolvimento ágil.

### TEMA 2

Um workflow do GitHub Actions tem processos definidos, como:

- Os Workflows: Que são definidos em arquivos YAML, contendo uma ou mais tarefas a serem executadas.
- Os Events: São eventos que disparam a execução do workflow, como push, pull request, ou cron schedules.
- As Secrets: São usadas para armazenar valores como chaves de acesso, região das instâncias, etc.
- As Actions: São tarefas reutilizáveis que realizam ações específicas, como executar comandos, configurar ambientes ou interagir com serviços externos.

### TEMA 3

AWS CloudFormation permite a criação e configuração de infraestrutura na AWS usando templates de código. Isso garante consistência, automação, e gerenciamento simplificado de recursos. O template que está sendo utilizado no projeto está dessa forma:

```yaml
AWSTemplateFormatVersion: '2010-09-09'
Resources:
  MyEC2Instance:
    Type: 'AWS::EC2::Instance'
    Properties:
      InstanceType: 't2.micro'
      KeyName: 'my-key-pair'
      ImageId: 'ami-0abcdef1234567890'
      SecurityGroups:
        - 'my-security-group'
Outputs:
  InstanceId:
    Description: 'ID da instância EC2'
    Value: !Ref MyEC2Instance

```

Esses template de AWS CloudFormation define a infraestrutura em código para criar e gerenciar recursos na AWS. No exemplo, o template começa especificando a versão do formato do CloudFormation. A seção de recursos `Resources` define uma instância EC2 chamada `MyEC2Instance`. Esse recurso é configurado com propriedades como o tipo de instância `t2.micro`, o par de chaves SSH (`my-key-pair`), a AMI específica `ami-0abcdef1234567890`, e o grupo de segurança `my-security-group`. A seção de saídas `Outputs` define uma saída chamada `InstanceId`, que fornece o ID da instância EC2 criada.

### TEMA 4

A integração de GitHub Actions com AWS CloudFormation e Amazon EC2 permite automação completa do deploy da nossa aplicação. Com a implementação da criação de pipelines CI/CD que automatizam a construção, teste, e deploy de aplicações, todo o desenvolvimento se torna mais fácil e ágil.

Ao aplicar essa integração em projetos reais, é possível obter um fluxo de trabalho contínuo e ininterrupto, onde cada alteração no código é automaticamente testada, construída e implantada em um ambiente de produção ou de teste. Isso permite a identificação e correção de problemas rapidamente, além de garantir que o código em produção esteja sempre atualizado e funcional.

Desafios Encontrados:
- Gerenciamento de Credenciais: O armazenamento de credenciais de forma segura, evitando exposição de informações sensíveis foi um desafio a ser superado, solucionamos utilizando o GitHub Secrets para armazenar chaves de acesso AWS de forma segura.
- Sincronização de Estados: Garantir que a infraestrutura esteja sempre em um estado consistente, mesmo em caso de falhas durante o deploy foi um desafio e foi solucionada com a implementação de verificações de integridade e mecanismos de rollback automáticos utilizando AWS S3 para armazenar o estado da infraestrutura.

Esses desafios foram inicialmente complicados devido ao pouco conhecimento técnico sobre as ferramentas. Porém utilizando a documentação das plataformas, foi possível contornar os desafios.

Então, a integração de GitHub Actions com AWS CloudFormation e Amazon EC2 não apenas automatiza o processo de deploy, mas também aumenta a confiabilidade e a eficiência do desenvolvimento de software.