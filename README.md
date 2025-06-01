# Aplicação Cliente API Embrapa Vitivinicultura

Este projeto implementa uma aplicação cliente que consome dados da API da Embrapa Vitivinicultura, realizando análises sobre importações e exportações por tipo de uva. A aplicação inclui autenticação, coleta de dados em tempo real, análise agregada e visualização interativa.

![Diagrama da Arquitetura](docs/diagrama_arquitetura.png)

## Funcionalidades

- **Autenticação**: Registro e login de usuários para obter token JWT
- **Coleta de Dados**: Consulta à API da Embrapa para obter dados de importações e exportações
- **Análise Agregada**: Processamento e agregação dos dados por tipo de uva
- **Visualização Interativa**: Interface web com tabelas e gráficos para análise visual

## Estrutura do Projeto

```
embrapa_app/
├── fetch_data.py                    # Script Python para autenticação e coleta de dados
├── analise_agregada_tipo_uva.csv    # Dados agregados por tipo de uva
├── client/                          # Interface cliente React
│   ├── src/                         # Código-fonte da interface
│   │   ├── App.tsx                  # Componente principal
│   │   └── components/              # Componentes reutilizáveis
│   │       └── DataTable.tsx        # Componente de tabela de dados
│   ├── public/                      # Arquivos públicos
│   │   └── data/                    # Dados para visualização
│   └── ...                          # Outros arquivos de configuração
├── docs/                            # Documentação
│   └── diagrama_arquitetura.png     # Diagrama da arquitetura
├── Dockerfile                       # Configuração para containerização
├── docker-compose.yml               # Configuração para orquestração de containers
└── README.md                        # Este arquivo
```

## Requisitos

### Para execução local

- Python 3.8+
- Node.js 16+
- npm ou pnpm

### Dependências Python

- requests
- pandas
- tqdm

### Dependências JavaScript

- react
- recharts
- react-papaparse

## Instalação e Execução

### 1. Configuração do Backend (Python)

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/embrapa-vitivinicultura.git
cd embrapa-vitivinicultura

# Instale as dependências Python
pip install requests pandas tqdm

# Execute o script de coleta de dados
python fetch_data.py
```

O script irá:
1. Registrar um usuário temporário na API
2. Realizar login para obter o token JWT
3. Coletar dados de importações e exportações
4. Agregar os dados por tipo de uva
5. Salvar o resultado em `analise_agregada_tipo_uva.csv`

### 2. Configuração do Frontend (React)

```bash
# Navegue até o diretório do cliente
cd client

# Instale as dependências
npm install
# ou
pnpm install

# Execute o servidor de desenvolvimento
npm run dev
# ou
pnpm run dev
```

Acesse a interface em `http://localhost:5173`

### 3. Usando Docker (Recomendado)

Para facilitar a execução, você pode usar Docker:

```bash
# Construa e inicie os containers
docker-compose up -d

# Acesse a interface em http://localhost:8080
```

## Uso da Aplicação

1. **Visualização em Tabela**: Exibe os dados agregados por tipo de uva
2. **Gráfico de Barras**: Compara valores de importação e exportação
3. **Gráficos de Pizza**: Mostra a distribuição percentual de importações e exportações

## Detalhes da API

A API da Embrapa Vitivinicultura requer autenticação via token JWT. Os principais endpoints são:

- `/register`: Registro de novos usuários
- `/login`: Autenticação e obtenção de token
- `/importacoes`: Dados de importação por ano e tipo
- `/exportacoes`: Dados de exportação por ano e tipo

Parâmetros obrigatórios para consultas:
- `ano`: Ano da consulta (1970-2023)
- `tipo`: Tipo de uva (vinhos-de-mesa, espumantes, uvas-frescas, uvas-passas, suco-de-uva)

## Contribuição

Para contribuir com este projeto:

1. Faça um fork do repositório
2. Crie uma branch para sua feature (`git checkout -b feature/nova-feature`)
3. Commit suas mudanças (`git commit -m 'Adiciona nova feature'`)
4. Push para a branch (`git push origin feature/nova-feature`)
5. Abra um Pull Request

## Licença

Este projeto está licenciado sob a licença MIT - veja o arquivo LICENSE para detalhes.

## Contato

Para dúvidas ou sugestões, abra uma issue no repositório do GitHub.
