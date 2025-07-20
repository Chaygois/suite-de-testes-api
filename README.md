🚀 Automação de Testes para API Fake Store
Este repositório apresenta uma solução completa para automação de testes de API focada na API Fake Store. Utilizamos o Postman para a criação dos testes, o Newman para execução via linha de comando e o GitHub Actions para garantir a Integração Contínua (CI).

✨ Funcionalidades
Testes de API Robustos: Uma coleção abrangente de testes desenvolvida no Postman para validar os endpoints da API Fake Store, garantindo a qualidade e o correto funcionamento.

Execução Local Flexível: Capacidade de executar todos os testes localmente via Newman, com a opção de utilizar variáveis de ambiente para diferentes cenários.

Relatórios Detalhados: Geração de relatórios HTML completos e de fácil leitura, permitindo uma análise profunda dos resultados dos testes e identificação rápida de falhas.

Integração Contínua (CI): Um workflow configurado no GitHub Actions que automatiza a execução dos testes em cada push e pull request, assegurando que a cada alteração o projeto continue estável.

Gerenciamento de Dependências: Uso do package.json para simplificar a instalação e execução das dependências necessárias para os testes.

📂 Estrutura do Projeto
A estrutura do projeto foi pensada para facilitar a organização e manutenção:

SUITE-DE-TESTES-API/
├── postman/
│   ├── fake-store-api-qa-automation.postman_collection.json # Coleção Postman com os testes da API
│   └── fake-store-env.json                                # Ambiente para variáveis (opcional)
├── reports/
│   └── fake-store-api-qa-automation-report.html           # Relatórios HTML gerados após a execução
├── .github/
│   └── workflows/
│       └── api-tests.yml                                  # Workflow para CI no GitHub Actions
├── README.md                                              # Documentação principal do projeto
├── package.json                                           # Configuração das dependências e scripts npm
└── .gitignore                                             # Arquivos ignorados pelo Git
💻 Como Executar os Testes Localmente
Siga os passos abaixo para rodar os testes em sua máquina.

Requisitos
Certifique-se de ter os seguintes softwares instalados:

Node.js: Versão recomendada: 14+ (inclui npm). Baixe em: nodejs.org.

Newman: Uma ferramenta de linha de comando do Postman. Pode ser instalado globalmente ou localmente.

Passo 1: Clonar o Repositório
Primeiro, clone este repositório para sua máquina local e navegue até o diretório do projeto:

Bash

git clone https://github.com/seu-usuario/SUITE-DE-TESTES-API.git
cd SUITE-DE-TESTES-API
Passo 2: Instalar Dependências
Se você não tiver o Newman instalado globalmente, o package.json já está configurado para instalá-lo localmente como uma dependência de desenvolvimento.

Execute o comando abaixo para instalar todas as dependências:

Bash

npm install
Passo 3: Executar os Testes
Você pode executar os testes diretamente com o Newman ou através de um script npm, que é mais prático.

Opção A: Executar diretamente com Newman
Bash

newman run postman/fake-store-api-qa-automation.postman_collection.json \
  -e postman/fake-store-env.json \
  -r cli,html --reporter-html-export reports/fake-store-api-qa-automation-report.html
-e postman/fake-store-env.json: O arquivo de ambiente é opcional. Utilize se sua coleção Postman depender de variáveis de ambiente.

-r cli,html: Gera um relatório na linha de comando e um relatório HTML.

--reporter-html-export reports/fake-store-api-qa-automation-report.html: Define o caminho e o nome do arquivo para o relatório HTML.

Opção B: Executar via script npm (Recomendado)
O package.json inclui um script para facilitar a execução dos testes:

Bash

npm test
Este comando executa exatamente o mesmo comando Newman descrito acima, de forma mais concisa.

Passo 4: Verificar o Relatório
Após a execução, um relatório HTML detalhado será gerado no diretório reports/.

reports/fake-store-api-qa-automation-report.html
Abra este arquivo em qualquer navegador web para analisar os resultados detalhados dos testes, incluindo o status de cada requisição, tempos de resposta e quaisquer falhas de asserção.

⚙️ Integração Contínua com GitHub Actions
O projeto está configurado para CI/CD utilizando GitHub Actions, garantindo que os testes sejam executados automaticamente em eventos chave no repositório.

Local do Workflow
O arquivo do workflow está localizado em:

.github/workflows/api-tests.yml
Gatilhos
O pipeline de CI é acionado automaticamente nos seguintes eventos:

push: Em todos os pushes para as branches main e master.

pull_request: Em todas as pull requests abertas contra as branches main e master.

O que o Workflow Faz
O workflow api-tests.yml executa as seguintes etapas:

Checkout do Código: Clona o repositório para o ambiente de execução do GitHub Actions.

Configuração do Node.js: Configura o ambiente Node.js necessário para o Newman.

Instalação do Newman: Instala o Newman e suas dependências.

Execução da Coleção Postman: Executa a coleção de testes Postman usando o Newman, gerando o relatório HTML.

Upload do Relatório: O relatório HTML gerado é carregado como um "artefato" da ação, podendo ser baixado e revisado diretamente na interface do GitHub Actions.

📦 Gerenciamento de Dependências e Scripts
O arquivo package.json gerencia as dependências do projeto e define scripts convenientes:

devDependencies: newman e newman-reporter-html são listados aqui, pois são ferramentas de desenvolvimento e teste, não para uso em produção.

scripts:

"test": Define o comando para executar os testes com Newman, conforme detalhado na seção "Como Executar os Testes Localmente".

Para instalar todas as dependências do projeto (incluindo as de desenvolvimento, como Newman), execute:

Bash

npm install
🤝 Contribuições
Contribuições são muito bem-vindas! Se você deseja colaborar com este projeto, siga os passos abaixo:

Faça um Fork deste repositório para sua própria conta no GitHub.

Crie uma Nova Branch para sua funcionalidade ou correção:

Bash

git checkout -b minha-nova-feature
Faça suas alterações e teste-as localmente.

Faça Commit das suas alterações com uma mensagem clara e descritiva:

Bash

git commit -m 'feat: Adicionados testes para endpoint de usuários'
Envie sua branch para seu repositório bifurcado:

Bash

git push origin minha-nova-feature
Abra um Pull Request no repositório original. Descreva detalhadamente as alterações feitas e por que elas são necessárias.

