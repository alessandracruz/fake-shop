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

## 📌 **Próximos Passos**

- Expandir o projeto com CI/CD utilizando **GitHub Actions**.
- Implementar monitoramento da aplicação com **Prometheus** e **Grafana**.
