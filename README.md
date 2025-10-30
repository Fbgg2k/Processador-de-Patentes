# Processador de Patentes

Este projeto processa arquivos HTML de patentes e gera um relatório consolidado em formato HTML.

## Pré-requisitos

- Python 3.6 ou superior
- pip (gerenciador de pacotes do Python)

## Configuração do Ambiente

1. Clone o repositório ou baixe os arquivos para sua máquina

2. Crie um ambiente virtual (recomendado):
   ```bash
   python -m venv venv
   ```

3. Ative o ambiente virtual:
   - No Linux/macOS:
     ```bash
     source venv/bin/activate
     ```
   - No Windows:
     ```
     .\venv\Scripts\activate
     ```

4. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```

## Executando o Script

1. Certifique-se de que o diretório `PATENTES` contendo os arquivos HTML de entrada está na pasta `src/`

2. Execute o script principal:
   ```bash
   python src/solution.PY
   ```

3. O script irá:
   - Processar todos os arquivos HTML no diretório `PATENTES`
   - Gerar um arquivo de saída em `src/templates/PATENTES.HTML`

## Visualizando o Resultado

Após a execução do script, você pode visualizar o relatório de duas maneiras:

1. **Navegador Web**
   - Abra o arquivo `src/templates/PATENTES.HTML` diretamente no seu navegador
   - No terminal, você pode usar:
     - Linux:
       ```bash
       xdg-open src/templates/PATENTES.HTML
       ```
     - macOS:
       ```bash
       open src/templates/PATENTES.HTML
       ```
     - Windows:
       ```
       start src\templates\PATENTES.HTML
       ```

2. **Servidor HTTP simples**
   - Navegue até a pasta do projeto e execute:
     ```bash
     cd src/templates
     python -m http.server 8000
     ```
   - Abra o navegador e acesse: http://localhost:8000/PATENTES.HTML

## Estrutura de Arquivos

- `src/SOLUTION.PY` - Script principal que processa as patentes
- `src/PATENTES/` - Diretório contendo os arquivos HTML de entrada
- `src/templates/PATENTES.HTML` - Arquivo de saída gerado
- `requirements.txt` - Dependências do projeto

## Testes do Projeto

O projeto inclui testes unitários abrangentes para garantir a qualidade e confiabilidade do código. A cobertura atual de testes é de **84%**, conforme mostrado no relatório de cobertura.

### Tipos de Testes Implementados

1. **Teste de Extração de Dados**
   - Verifica se a função `extract_patent_data` consegue extrair corretamente os dados de um arquivo HTML de patente
   - Testa a estrutura dos dados retornados e a correta extração de campos como número do pedido, data de depósito, título e IPC

2. **Teste de Arquivo Vazio**
   - Verifica o comportamento do sistema quando um arquivo HTML vazio é processado
   - Garante que o sistema lida corretamente com arquivos sem dados de patente

3. **Teste de Processamento em Lote**
   - Testa a função `process_patents` para garantir que ela processa corretamente múltiplos arquivos
   - Verifica a contagem correta de patentes processadas

4. **Teste de Geração de HTML**
   - Verifica se a função `generate_html_output` gera corretamente o arquivo HTML de saída
   - Confirma que o HTML gerado contém todos os dados esperados

### Como Executar os Testes

#### Pré-requisitos
- Python 3.7+
- Dependências do projeto instaladas (veja a seção de instalação)

#### Executando Todos os Testes

1. Navegue até o diretório do projeto:
   ```bash
   cd /home/bfelipef/Documentos/desafio/OpenSense/Opensense-proficiency-PATENTES
   ```

2. Ative o ambiente virtual (se aplicável):
   ```bash
   source venv/bin/activate
   ```

3. Execute os testes com cobertura:
   ```bash
   cd src
   python -m pytest --cov=. tests/
   ```

#### Opções de Execução

- Executar testes com saída detalhada:
  ```bash
  python -m pytest -v tests/
  ```

- Executar um teste específico:
  ```bash
  python -m pytest tests/test_solution.py::TestSolution::test_extract_patent_data_success -v
  ```

- Gerar relatório de cobertura em HTML:
  ```bash
  python -m pytest --cov=. --cov-report=html tests/
  ```

### Cobertura de Testes

O relatório de cobertura mostra que:
- `solution.py`: 70% de cobertura
- `test_solution.py`: 99% de cobertura
- Cobertura total: 84%

### Por que Testes São Importantes

1. **Qualidade do Código**: Garantem que o código funcione conforme o esperado
2. **Refatoração Segura**: Permitem fazer alterações no código com confiança
3. **Documentação Viva**: Servem como documentação do comportamento esperado do sistema
4. **Integração Contínua**: Facilitam a implementação de pipelines de CI/CD

## Solução de Problemas Comuns

### Erro: "python: command not found"
Use `python3` em vez de `python`:
```bash
python3 -m pytest src/tests/ -v
```

### Erro: Módulos não encontrados
Certifique-se de que as dependências estão instaladas:
```bash
pip install -r requirements.txt
```

### Erro: Nenhum arquivo encontrado
Verifique se os arquivos de teste estão no local correto:
- Arquivos de teste: `src/tests/test_*.py`
- Arquivos de patentes: `src/PATENTES/*.html`

### Erro de codificação
Se encontrar erros de codificação, verifique se os arquivos de entrada estão em ISO-8859-1

### Ainda com problemas?
Execute o script principal primeiro para garantir que os dados de teste estão corretos:
```bash
python3 src/SOLUTION.PY
```

## Licença

Este projeto está licenciado sob a licença MIT.
