Automação de Testes para a API Fake Store
Este repositório contém uma solução completa para automação de testes de API para a Fake Store API, utilizando Postman para a criação dos testes, Newman para execução via linha de comando, e GitHub Actions para integração contínua (CI).

 Funcionalidades
Testes de API Robustos: Coleção de testes desenvolvida no Postman para validar os endpoints da Fake Store API.

Execução Local Flexível: Capacidade de executar os testes localmente via Newman, com ou sem variáveis de ambiente.

Relatórios Detalhados: Geração de relatórios HTML abrangentes para análise dos resultados dos testes.

Integração Contínua (CI): Workflow configurado no GitHub Actions para execução automática dos testes em cada push e pull request.

Gerenciamento de Dependências: Uso de package.json para facilitar a instalação e execução dos testes.

📂 Estrutura do Projeto
SUITE-DE-TESTES-API/
├── postman/
│ ├── fake-store-api-qa-automation.postman_collection.json # Coleção Postman com os testes
│ └── fake-store-env.json                                # Ambiente para variáveis (opcional)
│
├── reports/                                               # Relatórios gerados após execução dos testes
│ └── fake-store-api-qa-automation-report.html
│
├── .github/
│ └── workflows/
│ └── api-tests.yml                                    # Workflow para CI no GitHub Actions
│
├── README.md                                              # Documentação do projeto
├── package.json                                           # Configuração das dependências e scripts npm
└── .gitignore                                             # Arquivos ignorados pelo Git

Como Executar os Testes Localmente
Requisitos
Certifique-se de ter os seguintes softwares instalados em sua máquina:

Node.js: Versão recomendada: 14+ (inclui npm). Você pode baixar em nodejs.org.

Newman: A ferramenta de linha de comando do Postman. Pode ser instalado globalmente ou localmente.

Passo 1: Clonar o Repositório
git clone https://github.com/seu-usuario/SUITE-DE-TESTES-API.git
cd SUITE-DE-TESTES-API

Passo 2: Instalar Dependências (Newman)
Se você não tiver o Newman instalado globalmente, o package.json já está configurado para instalá-lo localmente como uma dependência de desenvolvimento.

npm install

Passo 3: Executar os Testes
Você pode executar os testes diretamente com o Newman ou através de um script npm.

Opção A: Executar diretamente com Newman
newman run postman/fake-store-api-qa-automation.postman_collection.json \
  -e postman/fake-store-env.json \
  -r cli,html --reporter-html-export reports/fake-store-api-qa-automation-report.html

-e postman/fake-store-env.json: O arquivo de ambiente é opcional. Utilize-o se sua coleção Postman depender de variáveis de ambiente.

-r cli,html: Gera um relatório na linha de comando e um relatório HTML.

--reporter-html-export reports/fake-store-api-qa-automation-report.html: Define o caminho e o nome do arquivo para o relatório HTML.

Opção B: Executar via script npm
O package.json inclui um script para facilitar a execução dos testes:

npm test

Este comando executa exatamente o mesmo comando Newman descrito acima.

Passo 4: Verificar o Relatório
Após a execução, um relatório HTML detalhado será gerado no diretório reports/.

reports/fake-store-api-qa-automation-report.html

Abra este arquivo em qualquer navegador web para analisar os resultados detalhados dos testes, incluindo status de cada requisição, tempos de resposta e falhas de asserção.

⚙️ Integração Contínua com GitHub Actions
O projeto está configurado para CI/CD utilizando GitHub Actions, garantindo que os testes sejam executados automaticamente em eventos chave no repositório.

Local do Workflow
O arquivo do workflow está localizado em:

.github/workflows/api-tests.yml

Gatilhos
O pipeline CI é acionado automaticamente em:

push: Em todos os pushes para as branches main e master.

pull_request: Em todas as pull requests abertas contra as branches main e master.

O que o Workflow Faz
O workflow api-tests.yml executa as seguintes etapas:

Checkout do Código: Clona o repositório para o ambiente de execução do GitHub Actions.

Setup do Node.js: Configura o ambiente Node.js necessário para o Newman.

Instalação do Newman: Instala o Newman e suas dependências.

Execução da Coleção Postman: Executa a coleção de testes Postman usando o Newman, gerando o relatório HTML.

Upload do Relatório: O relatório HTML gerado é carregado como um "artifact" da ação, podendo ser baixado e revisado diretamente na interface do GitHub Actions.

📦 Gerenciamento de Dependências e Scripts
O arquivo package.json gerencia as dependências do projeto e define scripts convenientes:

dependencies: Não são usadas diretamente, mas newman e newman-reporter-html são listadas como devDependencies.

scripts:

"test": Define o comando para executar os testes com Newman, como detalhado na seção "Como Executar os Testes Localmente".

Para instalar todas as dependências do projeto (incluindo as de desenvolvimento, como Newman), execute:

npm install

🤝 Contribuições
Contribuições são muito bem-vindas! Se você deseja colaborar com este projeto, siga os passos abaixo:

Faça um Fork deste repositório para sua própria conta do GitHub.

Crie uma Nova Branch para sua feature ou correção:

git checkout -b minha-nova-feature

Faça suas Alterações e teste-as localmente.

Faça Commit das suas alterações com uma mensagem clara e descritiva:

git commit -m 'feat: Adiciona testes para endpoint de usuários'

Envie sua Branch para o seu repositório bifurcado:

git push origin minha-nova-feature

Abra um Pull Request no repositório original. Descreva detalhadamente as alterações feitas e por que elas são necessárias.