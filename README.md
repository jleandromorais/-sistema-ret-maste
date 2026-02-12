# 🚀 Sistema RET Master

[![Python](https://img.shields.io/badge/Python-3.14-blue.svg)](https://python.org)
[![CustomTkinter](https://img.shields.io/badge/CustomTkinter-5.2+-green.svg)](https://github.com/TomSchimansky/CustomTkinter)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-2.0-orange.svg)](CHANGELOG.md)

> **Sistema moderno e profissional para processamento automatizado de PDFs de RET (Receita de Encargos e Tarifas)**

Interface gráfica avançada com CustomTkinter, extração inteligente de dados e exportação para Excel profissionalmente formatado.

---

## 📸 Preview

```
┌──────────────────────────────────────────────────────────────┐
│  🚀 Sistema RET Master    Processamento Automatizado        │
├────────────────┬──────────────────────────────────────────┤
│  SELEÇÃO       │  RESULTADOS                              │
│                │  ┌────────────────────────────────┐      │
│  📁 Pasta      │  │ Resumo │ Dados │ Logs │       │      │
│  ☑ EAT         │  ├────────────────────────────────┤      │
│  ☑ Penalidades │  │  PDFs: 35                      │      │
│  ☑ TOP         │  │  Valores: 261                  │      │
│                │  │  Total: EUR 92M+               │      │
│  ▶ PROCESSAR   │  └────────────────────────────────┘      │
├────────────────┴──────────────────────────────────────────┤
│  💰 TOTAL: EUR 92,036,573.52    💾 Salvar  📊 Exportar    │
└──────────────────────────────────────────────────────────────┘
```

---

## ✨ Funcionalidades Principais

### 🎨 Interface Moderna
- Design escuro e profissional com CustomTkinter
- Layout intuitivo com painéis organizados
- Visualização em tempo real do processamento
- Sistema de abas para diferentes visualizações

### 📊 Processamento Inteligente
- Extração automática de dados estruturados dos PDFs
- Identificação automática de:
  - ✅ Tipo de Encargo (EAT, Penalidades, TOP)
  - ✅ Empresa
  - ✅ Tipo de Nota (Débito/Crédito)
  - ✅ Número da ND
  - ✅ Data de Vencimento
  - ✅ Valor Total
  - ✅ Quantidade (QT)
  - ✅ Valor Unitário

### 📁 Arquivos Gerados

#### 1. Excel Profissional (RET_Relatorio.xlsx)
Arquivo Excel com **formatação profissional** contendo 3 abas:

**📋 Dados Completos**
- Tabela completa com todos os registros
- Cabeçalhos formatados (azul escuro com texto branco)
- Bordas em todas as células
- Formatação numérica automática
- Larguras de coluna ajustadas
- Alinhamento centralizado

Colunas:
1. Tipo de Encargo
2. Empresa
3. Nota Débito/Crédito
4. Nº
5. Data Vencimento
6. Valor Total
7. QT
8. Valor Unitário
9. Arquivo

**📊 Resumo por Tipo**
- Agrupamento por tipo de encargo
- Somatórios automáticos
- Contagem de arquivos
- Formatação visual destacada

**📈 Resumo Geral**
- Estatísticas globais
- Total de PDFs processados
- Quantidade total
- Valor total em EUR
- Data e hora do processamento

#### 2. Banco de Dados SQLite (RET_dados.db)
Banco de dados completo com tabela `dados_ret` contendo:
- ID automático
- Todos os campos extraídos
- Timestamps de processamento
- Caminhos completos dos arquivos

## 🎯 Como Usar

### 1. Executar o Sistema

```powershell
# Ativar ambiente virtual
.\venv\Scripts\Activate.ps1

# Executar
python Somatorio_De_Ret.py
```

### 2. Interface Principal

**Painel Esquerdo - Controles:**
- 📁 **Selecionar Pasta**: Escolha a pasta raiz contendo os PDFs
- ☑️ **Tipos de Encargo**: Marque os tipos que deseja processar
  - EAT (Encargos de Acesso e Transporte)
  - Penalidades
  - TOP (Takeoff Point)
- ▶️ **PROCESSAR PDFs**: Inicia o processamento

**Painel Direito - Resultados:**
- 📊 **Resumo**: Estatísticas gerais e por tipo
- 📋 **Dados Detalhados**: Visualização tabular dos dados
- 📝 **Logs**: Acompanhamento em tempo real

**Rodapé:**
- 💰 **Total Geral**: Valor total processado em destaque
- 💾 **Salvar no Banco**: Grava dados no SQLite
- 📊 **Exportar Excel**: Gera relatório Excel formatado

## 🎨 Características Visuais

### Cores do Tema
- **Fundo Principal**: Escuro moderno
- **Destaques**: Azul ciano (#00d9ff)
- **Botão Processar**: Verde (#4CAF50)
- **Botão Salvar**: Roxo (#9C27B0)
- **Botão Excel**: Laranja (#FF9800)

### Tipografia
- **Fonte Principal**: Roboto
- **Logs**: Consolas (monoespaçada)
- **Tamanhos**: Responsivos (10-32pt)

## 📋 Estrutura de Dados Extraídos

Cada PDF processado gera um registro com:

| Campo | Descrição | Exemplo |
|-------|-----------|---------|
| **Tipo de Encargo** | EAT/Penalidades/TOP | EAT |
| **Empresa** | Nome da empresa | COPERGAS |
| **Nota Débito/Crédito** | Tipo de nota | Débito |
| **Nº** | Número da ND | 0917167397 |
| **Data Vencimento** | Data no formato DD/MM/AAAA | 15/12/2025 |
| **Valor Total** | Valor total em EUR | 26524.62 |
| **QT** | Quantidade | 1000 |
| **Valor Unitário** | Valor por unidade | 26.52 |
| **Arquivo** | Nome do PDF | ND_355.pdf |

## 🔧 Requisitos Técnicos

### Dependências
```
pandas>=3.0.0
openpyxl>=3.1.5
pdfplumber>=0.11.9
PyPDF2>=3.0.1
customtkinter>=5.2.2
pillow>=12.1.1
darkdetect>=0.8.0
```

### Instalação
```powershell
python -m pip install -r requirements.txt
```

## 📊 Exemplo de Processamento

### Entrada
```
C:\Desktop\RET\
├── EAT\
│   └── 12 EAT dez-25\
│       └── Extraido\
│           ├── ND_355.pdf
│           ├── ND_0917167397.pdf
│           └── ...
├── Penalidades\
│   └── 12 PEN dez-25\
│       └── Extraido\
│           ├── AMBEV_NDPFP03808.pdf
│           └── ...
└── TOP\
    └── 12 TOP dez-25\
        └── Extraido\
            └── ...
```

### Saída
- ✅ **RET_Relatorio.xlsx** (Excel profissionalmente formatado)
- ✅ **RET_dados.db** (Banco de dados SQLite)
- ✅ **Logs completos** na interface
- ✅ **Estatísticas detalhadas** por tipo

## 🎯 Diferenciais

### ✨ Interface
- ✅ Design moderno e profissional
- ✅ Dark mode nativo
- ✅ Responsiva e intuitiva
- ✅ Feedback visual em tempo real

### 📊 Excel
- ✅ Formatação profissional
- ✅ Cores e bordas
- ✅ Múltiplas abas organizadas
- ✅ Fórmulas e totalizadores
- ✅ Larguras ajustadas automaticamente

### 🔍 Processamento
- ✅ Extração inteligente de dados
- ✅ Detecção automática de empresas
- ✅ Identificação de tipos de nota
- ✅ Cálculos automáticos
- ✅ Tratamento de erros robusto

## 🐛 Troubleshooting

### Interface não abre
```powershell
# Reinstalar CustomTkinter
pip install --upgrade --force-reinstall customtkinter
```

### Erros de encoding
- O sistema trata automaticamente caracteres especiais
- Logs usam formato seguro para Windows

### PDFs não encontrados
- Verifique se a pasta selecionada contém subpastas com PDFs
- Os PDFs devem ter extensão .pdf (minúscula ou maiúscula)

## 📞 Informações

**Desenvolvido em**: Python 3.14  
**Framework UI**: CustomTkinter 5.2+  
**Data**: Fevereiro 2026  

---

## 🎉 Novidades desta Versão

### v2.0 - Interface Moderna
- ✨ Interface completamente redesenhada com CustomTkinter
- 📊 Excel com formatação profissional
- 🎨 Cores e temas modernos
- 📋 Campos estruturados completos
- 💾 Sistema de banco de dados aprimorado
- 📈 Múltiplas visualizações (Resumo, Dados, Logs)
- ⚡ Performance otimizada

**Aproveite o sistema!** 🚀
