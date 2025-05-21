[![deploy](https://github.com/alisonpezzott/merge_pbi_reports_sample/actions/workflows/deploy.yml/badge.svg)](https://github.com/alisonpezzott/merge_pbi_reports_sample/actions/workflows/deploy.yml)  
 

# Workflow de Projetos Power BI

## O que é isso?  

Este repositório é um exemplo de como trabalhar em colaboração com projetos Power BI utilizando Git e GitHub Workflow, resolvendo conflitos e construindo um projeto paralelo de exemplo.  
Ele demonstra o uso de um cenário de CI/CD para projetos Microsoft Power BI PRO utilizando o [fabric-cli](https://aka.ms/fabric-cli) e GitHub Actions.  


## Links Rápidos  
- Demonstração em vídeo deste repositório: https://youtu.be/sgVqrOUgXro  
- Como obter um Service Principal: https://youtu.be/IFp1Aingnmw  
- Aprenda Git e GitHub para MS Fabric e Power BI: https://youtu.be/wFimCGpndOc  


## Instalação  

- Faça um fork deste repositório  
- Crie uma cópia de `.env.example`, renomeie para `.env` e preencha com os segredos do SPN  
- Configure os mesmos segredos do SPN no GitHub Actions se desejar usar CD  


|Nome|Valor|  
|---|---|  
|FABRIC_CLIENT_ID|Seu ID do Cliente do Service Principal do Entra App ID|  
|FABRIC_CLIENT_SECRET|Seu Segredo do Service Principal do Entra App ID|  
|FABRIC_TENANT_ID|Seu ID do Tenant|  


Se for executar localmente, na primeira vez instale os requisitos com:  

```bash
$ pip install -r requirements.txt  
```

- Configure o arquivo `config.json` com os IDs por branch.  
  - Os `adminUPNs` são os IDs de Objeto do Nome Principal do Usuário do Entra.  


## Pipeline de CI/CD  

- Os projetos Power BI são salvos na pasta `src` com as extensões `*.Report` e `*.SemanticModel`.  
- O deploy de novas versões é feito no branch `dev`.  
- A cada Pull Request para o branch `develop`, o pipeline do GitHub Actions chamado `.github\workflows\bpa.yml` é acionado, executando a análise de melhores práticas. Esse processo utiliza ferramentas da comunidade como [Tabular Editor](https://github.com/TabularEditor/) e [PBI-Inspector](https://github.com/NatVanG/PBI-InspectorV2). Se aprovado e mesclado, o pipeline `.github\workflows\deploy.yml` fará o deploy para o workspace `*-DEV` com o nome e a fonte de dados especificados no `config.json`.  
- Após a aprovação do projeto, é criada uma pull request para o branch `main`, onde o pipeline fará o deploy da versão para o workspace `*-PRD`, seguindo o mesmo `config.json`.  


## Contribuindo  

- Se você gostaria de ajudar a financiar ou patrocinar o projeto, pode fazê-lo via [💗 GitHub Sponsors](https://github.com/sponsors/alisonpezzott) ou ainda via [YouTube](https://youtube.com/@alisonpezzott).  
- Esta é apenas uma abordagem sugerida em um mundo de inúmeras possibilidades e estruturas diversas.  
Você pode e deve usar este repositório como inspiração e base técnica para construir pipelines mais sofisticados e robustos, se necessário, para sua aplicação. Se você é um desenvolvedor e descobrir problemas ou maneiras alternativas, envie suas pull requests para apreciação caso deseje contribuir com código para o projeto.  
- Outras formas de contribuir são ajudando outras pessoas com suporte em nossos fóruns ou em nossa comunidade. Você pode acessá-los nos links abaixo.  

[![YouTube subscribers](https://img.shields.io/youtube/channel/subscribers/UCst_4Wi9DkGAc28uEPlHHHw?style=flat&logo=youtube&logoColor=ff0000&colorA=2E3440&colorB=FFFFFF)](https://www.youtube.com/@alisonpezzott?sub_confirmation=1)  
[![GitHub followers](https://img.shields.io/github/followers/alisonpezzott?style=flat&logo=github&logoColor=ffffff&colorA=2E3440&colorB=FFFFFF)](https://github.com/alisonpezzott)  
[![LinkedIn](https://custom-icon-badges.demolab.com/badge/LinkedIn-0A66C2?logo=linkedin-white&logoColor=fff)](https://linkedin.com/in/alisonpezzott)  
[![Discord](https://img.shields.io/badge/Discord-%235865F2.svg?&logo=discord&logoColor=white)](https://discord.gg/sJTDvWz9sM)  
[![Telegram](https://img.shields.io/badge/Telegram-2CA5E0?logo=telegram&logoColor=white)](https://t.me/alisonpezzott)  
[![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/alisonpezzott)  