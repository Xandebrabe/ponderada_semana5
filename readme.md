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
resource "aws_instance" "web" {
  ami                    = "ami-057f57c2fcd14e5f4"
  instance_type          = "t2.micro"
  security_groups        = [aws_security_group.default_security.name]

  user_data = <<-EOF
                #!/bin/bash
                sudo apt update
                sudo apt install -y docker.io
                sudo systemctl start docker
                sudo systemctl enable docker
              EOF

  tags = {
    Name = "WebServer"
  }
}
```

### TEMA 4

A integração de GitHub Actions com AWS CloudFormation e Amazon EC2 permite automação completa do deploy da nossa aplicação. Com a implementação da criação de pipelines CI/CD que automatizam a construção, teste, e deploy de aplicações, todo o desenvolvimento se torna mais fácil e ágil.

Desafios Encontrados:
- Gerenciamento de Credenciais: Utilização do GitHub Secrets para armazenar credenciais de forma segura.
- Sincronização de Estados: Implementar verificações de integridade e rollback automáticos, utilizando o s3.

Esses desafios estavam relacionados a pouco conhecimento técnico do assunto, porém utilizando a documentação das plataformas, foi possível contornar os desafios.