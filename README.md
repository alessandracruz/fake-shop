# **Fake Shop - Deploy na AWS com Kubernetes**

Este repositório contém o projeto **Fake Shop**, desenvolvido como parte do desafio da Semana DevOps. O objetivo principal desta etapa foi construir, entregar e gerenciar uma aplicação de e-commerce, utilizando o poder combinado do **Docker** e do **Kubernetes**, em um ambiente seguro e escalável na **AWS**, seguindo as melhores práticas DevOps.

## 📚 **Por que Kubernetes?**

O Kubernetes é uma ferramenta poderosa para orquestrar containers, como aqueles criados com Docker. Ele desempenha um papel essencial em ambientes modernos de desenvolvimento, permitindo:

- **Escalabilidade automática**: Kubernetes gerencia réplicas da sua aplicação para garantir disponibilidade, mesmo em caso de falhas.
- **Deploy ágil e seguro**: Permite a troca eficiente de versões da aplicação sem causar indisponibilidade.
- **Resiliência e estabilidade**: Detecta e reinicia containers com problemas automaticamente.
- **Gerenciamento centralizado**: Através de objetos como Deployments e Services, é possível orquestrar e manter aplicações complexas com facilidade.

Ao somar o Kubernetes com o Docker, você obtém o melhor dos dois mundos: a flexibilidade de criar containers padronizados com o Docker e a capacidade de gerenciá-los de forma eficiente e escalável com o Kubernetes.

Nesta etapa do desafio, aplicamos o Kubernetes para realizar o deploy da aplicação **Fake Shop** na nuvem, utilizando **AWS** como provedor.

------

## 📚 **Objetivo do Projeto**

Fechando mais um passo dessa solução DevOps, o objetivo desta etapa foi:

- **Criar um ambiente seguro e escalável** para uma aplicação de e-commerce usando Kubernetes.
- Utilizar a **AWS** para provisionar recursos e hospedar a aplicação.
- Demonstrar como **Docker e Kubernetes** tornam possível gerenciar containers de forma eficiente e confiável.
- Implementar o **Elastic Load Balancer (ELB)** para fornecer um ponto único de acesso à aplicação.

### 🛑 **Atenção: Custos na AWS**

Durante esta etapa, foi necessário criar uma conta na AWS com um cartão internacional, e os recursos utilizados **não estão no pacote gratuito**. Para evitar cobranças inesperadas, **apague os recursos criados ao final do projeto**, incluindo o cluster EKS e quaisquer serviços associados.

Para apagar o que foi feito no Kubernetes:

```
kubectl delete -f k8s/deployment.yaml
```

Passos recomendados no ambiente web AWS:

1. Exclua o Node groups no ambiente EKS
2. Exclua o cluster EKS criado.
3. Exclua a stack de rede no ambiente CloudFormation.
4. Certifique-se de que a conta não tenha recursos ativos que possam gerar cobranças.

------

## 🚀 **Deploy com Kubernetes**

1. Clone este repositório:

   ```
   git clone https://github.com/alessandracruz/fake-shop.git
   cd fake-shop
   ```

2. Aplique os manifestos do Kubernetes para criar o ambiente:

   ```
   kubectl apply -f k8s/deployment.yaml
   ```

3. Acesse a aplicação pelo Load Balancer gerado pela AWS (o endereço será exibido pelo Kubernetes).

------

## 🌟 **O que foi aprendido**

Nesta etapa, foram consolidados conhecimentos essenciais para o profissional DevOps:

- Configuração e uso de **Kubernetes** para deploys ágeis, escaláveis e resilientes.
- Orquestração de containers com **Docker** e **Kubernetes**.
- Utilização da AWS como provedor de nuvem, incluindo a criação de um cluster gerenciado (EKS).
- Integração de Load Balancers para disponibilizar a aplicação ao público.

------

### 🚀 **Pipeline CI/CD com GitHub Actions**

- Nesta etapa, configuramos uma **pipeline CI/CD** para o projeto **Fake Shop**, utilizando **GitHub Actions** como plataforma de automação. Essa pipeline representa um passo essencial na modernização do fluxo DevOps, unindo **integração contínua (CI)** e **entrega contínua (CD)** de maneira eficiente e confiável.

  #### **O que é o GitHub Marketplace?**

  O **GitHub Marketplace** é uma biblioteca de actions reutilizáveis, desenvolvidas por mantenedores confiáveis e pela comunidade, que permitem integrar funcionalidades avançadas à pipeline. Durante esta etapa, utilizamos actions prontas disponíveis no marketplace para:

  - **Autenticação no Docker Hub e AWS**.
  - **Construção e push de imagens Docker**.
  - **Deploy de manifestos no Kubernetes**.

  ------

  ### **O que foi Implementado?**

  #### **Integração Contínua (CI)**

  1. Checkout do Código:
     - Obtemos o código mais recente do repositório para iniciar o processo.
  2. Autenticação no Docker Hub:
     - Garante o acesso seguro ao Docker Hub para construção e publicação de imagens.
  3. Verificação do Ambiente:
     - Confirma a existência de arquivos críticos, como o `Dockerfile`, para evitar falhas na construção.
  4. Construção e Push da Imagem Docker:
     - Cria a imagem a partir do diretório `src` e a publica no Docker Hub com tags versionadas automaticamente.

  #### **Entrega Contínua (CD)**

  1. Autenticação na AWS:
     - Configuramos as credenciais para acessar o EKS (Elastic Kubernetes Service).
  2. Configuração do Kubernetes:
     - Atualizamos o contexto do `kubectl` para gerenciar o cluster na AWS.
  3. Deploy Automatizado:
     - Utilizamos ações para aplicar os manifestos Kubernetes, garantindo que a aplicação seja atualizada com a imagem mais recente.

  ------

  ### **Por que Isso é Importante?**

  - **Automação**: Elimina processos manuais, reduzindo erros e economizando tempo.
  - **Escalabilidade**: Facilita o deploy de versões mais recentes em ambientes complexos.
  - **Confiabilidade**: Testes e validações garantem a integridade da aplicação antes do deploy.
  - **Flexibilidade**: A pipeline pode ser estendida para incluir testes automatizados (unitários, integração e funcionais), análise de código e até mesmo monitoramento em tempo real.

  ------

  Essa abordagem prática demonstra como a **pipeline CI/CD** eleva o nível de entrega de software, garantindo qualidade, segurança e eficiência em cada etapa do ciclo de desenvolvimento.

------

### 📊 **Monitoramento com Prometheus e Grafana**

   - Configuração de um ambiente robusto de **monitoramento de aplicação** e **infraestrutura** utilizando **Prometheus** e **Grafana**.
   - Coleta de métricas da aplicação **Fake Shop** através de endpoints expostos.
   - Monitoramento detalhado do cluster Kubernetes, identificando possíveis pontos críticos e prevenindo problemas.
   - Criação de dashboards informativos para uma visão ampla do desempenho da aplicação e da infraestrutura.

   ------

   #### **Benefícios e Objetivos**

      - **Otimização:** Dashboards fornecem insights sobre o desempenho da aplicação e do ambiente, permitindo ajustes em tempo real.
      - **Confiabilidade:** Configuração de alertas para antecipar problemas e melhorar a experiência do cliente e do usuário.
      - **Escalabilidade:** Monitoramento centralizado garante que o sistema suporte crescimento sem perda de qualidade.

   ------

   #### **Exemplos Práticos**

   Os dashboards foram criados para:

      - Visualizar o tempo de resposta e o número de requisições da aplicação.
      - Monitorar a alocação de recursos dos pods no Kubernetes.
      - Configurar alertas, como consumo excessivo de CPU ou memória, e falhas nos serviços.

------

## 📌 **Próximos Passos** Possíveis

- Expandir o uso de alertas para diferentes cenários (ex.: disponibilidade, segurança).
- Integrar monitoramento com ferramentas de logs para uma análise mais detalhada de erros.
- Explorar integrações com serviços externos, como notificações para alertas automáticos.