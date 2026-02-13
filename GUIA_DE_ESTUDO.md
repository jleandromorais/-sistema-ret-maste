# 📚 GUIA DE ESTUDO - Sistema RET Master

## 🎯 Como Usar Este Material

Este guia foi criado para te ajudar a entender CADA PARTE do código do Sistema RET Master.

### 📁 Arquivos de Estudo

1. **`Somatorio_De_Ret_Comentado.py`** ← **COMECE AQUI!**
   - Código completo com comentários DETALHADOS
   - Explicações linha por linha
   - Conceitos técnicos explicados
   - 900+ linhas de documentação

2. **`GUIA_DE_ESTUDO.md`** ← **VOCÊ ESTÁ AQUI**
   - Roteiro de aprendizado
   - Conceitos organizados por tópico
   - Exercícios práticos
   - Recursos adicionais

---

## 🗺️ Mapa do Código

### 📦 Estrutura Geral

```
Sistema RET Master
│
├── 1️⃣ IMPORTAÇÕES (linhas 1-50)
│   ├── Bibliotecas de GUI
│   ├── Bibliotecas de PDF
│   ├── Bibliotecas de dados
│   └── Bibliotecas de Excel
│
├── 2️⃣ CONFIGURAÇÕES (linhas 51-100)
│   ├── Tema visual
│   └── Constantes globais
│
├── 3️⃣ CLASSE PRINCIPAL (linhas 100-900)
│   │
│   ├── 🏗️ Inicialização (__init__)
│   │   └── Configura janela e variáveis
│   │
│   ├── 🎨 Interface (_setup_ui)
│   │   ├── Header
│   │   ├── Painel Esquerdo (controles)
│   │   ├── Painel Direito (resultados)
│   │   └── Rodapé (ações)
│   │
│   ├── 🔍 Processamento de PDFs
│   │   ├── extrair_dados_pdf()
│   │   ├── _identificar_tipo()
│   │   ├── _extrair_empresa()
│   │   └── _extrair_tipo_nota()
│   │
│   ├── 📊 Visualização
│   │   ├── _mostrar_resultados()
│   │   └── _mostrar_dados_detalhados()
│   │
│   └── 💾 Exportação
│       ├── salvar_db()
│       └── exportar_excel()
│
└── 4️⃣ EXECUÇÃO (linhas 900-910)
    └── Inicia o app
```

---

## 📖 Roteiro de Aprendizado

### Nível 1: Iniciante 🌱

#### Dia 1: Entendendo a Estrutura Básica

**O que estudar:**
- Linhas 1-50: Importações
- Linhas 100-150: Construtor da classe

**Conceitos:**
- O que é uma biblioteca/módulo?
- O que é uma classe?
- O que é `__init__`?
- O que é `self`?

**Exercícios:**
1. Liste todas as bibliotecas usadas
2. Explique o que cada uma faz
3. Identifique onde `self` é usado
4. Crie uma classe simples similar

**Código de exemplo:**
```python
class MeuApp:
    def __init__(self):
        self.nome = "Meu Sistema"
        print(f"Iniciando: {self.nome}")

app = MeuApp()  # Executa __init__
```

---

#### Dia 2: Interface Gráfica Básica

**O que estudar:**
- Linhas 150-400: Função `_setup_ui()`

**Conceitos:**
- O que são widgets?
- Como funciona o `pack()`?
- O que é `command=`?

**Exercícios:**
1. Identifique todos os Buttons
2. Encontre todos os Labels
3. Liste todas as cores usadas
4. Crie uma janela simples

**Código de exemplo:**
```python
import customtkinter as ctk

janela = ctk.CTk()
janela.title("Meu App")

label = ctk.CTkLabel(janela, text="Olá!")
label.pack()

botao = ctk.CTkButton(
    janela,
    text="Clique",
    command=lambda: print("Clicou!")
)
botao.pack()

janela.mainloop()
```

---

### Nível 2: Intermediário 🌿

#### Dia 3-4: Processamento de PDFs

**O que estudar:**
- Linhas 400-600: Funções de extração

**Conceitos:**
- Como PDFPlumber funciona?
- O que é Regex?
- Como extrair padrões de texto?

**Exercícios:**
1. Rode os exemplos de regex no Python
2. Teste extrair texto de um PDF
3. Crie seus próprios padrões regex
4. Extrai um tipo de dado novo

**Código de exemplo:**
```python
import pdfplumber
import re

# Abrir PDF
with pdfplumber.open("arquivo.pdf") as pdf:
    # Ler primeira página
    texto = pdf.pages[0].extract_text()
    
    # Buscar CPF (exemplo)
    cpf = re.search(r'\d{3}\.\d{3}\.\d{3}-\d{2}', texto)
    print(cpf.group() if cpf else "Não encontrado")
```

---

#### Dia 5-6: Manipulação de Dados

**O que estudar:**
- Linhas 600-700: Processamento de listas

**Conceitos:**
- List comprehension
- Dicionários
- Pandas DataFrame
- Agregações

**Exercícios:**
1. Crie lista de dicionários
2. Converta para DataFrame
3. Faça agrupamentos
4. Calcule estatísticas

**Código de exemplo:**
```python
import pandas as pd

# Lista de dados
dados = [
    {'tipo': 'EAT', 'valor': 100},
    {'tipo': 'EAT', 'valor': 200},
    {'tipo': 'TOP', 'valor': 150},
]

# Converter para DataFrame
df = pd.DataFrame(dados)

# Agrupar e somar
resumo = df.groupby('tipo')['valor'].sum()
print(resumo)
```

---

### Nível 3: Avançado 🌳

#### Dia 7-8: Banco de Dados

**O que estudar:**
- Linhas 700-800: Função `salvar_db()`

**Conceitos:**
- SQL básico
- SQLite3
- CRUD operations
- Transações

**Exercícios:**
1. Crie banco simples
2. Insira dados
3. Faça consultas
4. Atualize registros

**Código de exemplo:**
```python
import sqlite3

# Conectar
conn = sqlite3.connect('teste.db')
cursor = conn.cursor()

# Criar tabela
cursor.execute('''
    CREATE TABLE IF NOT EXISTS usuarios (
        id INTEGER PRIMARY KEY,
        nome TEXT,
        idade INTEGER
    )
''')

# Inserir
cursor.execute(
    'INSERT INTO usuarios (nome, idade) VALUES (?, ?)',
    ('João', 30)
)

# Consultar
cursor.execute('SELECT * FROM usuarios')
print(cursor.fetchall())

conn.commit()
conn.close()
```

---

#### Dia 9-10: Excel Avançado

**O que estudar:**
- Linhas 800-900: Função `exportar_excel()`

**Conceitos:**
- OpenPyXL
- Formatação de células
- Múltiplas abas
- Estilos

**Exercícios:**
1. Crie Excel com OpenPyXL
2. Adicione formatação
3. Crie múltiplas abas
4. Adicione fórmulas

**Código de exemplo:**
```python
from openpyxl import Workbook
from openpyxl.styles import Font, PatternFill

wb = Workbook()
ws = wb.active

# Cabeçalho
ws['A1'] = 'Nome'
ws['B1'] = 'Valor'

# Formatação
ws['A1'].font = Font(bold=True)
ws['A1'].fill = PatternFill(
    start_color='1F4788',
    fill_type='solid'
)

# Dados
ws['A2'] = 'João'
ws['B2'] = 1000

wb.save('teste.xlsx')
```

---

## 🎓 Conceitos Fundamentais

### 1. POO (Programação Orientada a Objetos)

```python
# CLASSE = Molde
class Carro:
    def __init__(self, cor):
        self.cor = cor  # Atributo
    
    def buzinar(self):  # Método
        print("Beep!")

# OBJETO = Instância do molde
meu_carro = Carro("vermelho")
meu_carro.buzinar()  # Chama método
```

**No Sistema RET:**
- `SistemaRET` é a classe
- `app = SistemaRET()` cria o objeto
- `self.pasta_selecionada` é um atributo
- `self.processar()` é um método

---

### 2. Regex (Expressões Regulares)

```python
import re

texto = "Meu CPF é 123.456.789-00"

# Buscar padrão
resultado = re.search(r'\d{3}\.\d{3}\.\d{3}-\d{2}', texto)

if resultado:
    print(resultado.group())  # 123.456.789-00
```

**Padrões Comuns:**
- `\d` = dígito (0-9)
- `\d{3}` = exatamente 3 dígitos
- `\d+` = 1 ou mais dígitos
- `\d*` = 0 ou mais dígitos
- `.` = qualquer caractere
- `\.` = ponto literal
- `[0-9]` = dígito de 0 a 9
- `[a-z]` = letra minúscula
- `\s` = espaço
- `?` = opcional (0 ou 1)
- `*` = 0 ou mais
- `+` = 1 ou mais

---

### 3. List Comprehension

```python
# Modo tradicional
numeros_dobrados = []
for x in [1, 2, 3, 4, 5]:
    numeros_dobrados.append(x * 2)

# List comprehension (mais Pythônico)
numeros_dobrados = [x * 2 for x in [1, 2, 3, 4, 5]]

# Com condição
pares = [x for x in range(10) if x % 2 == 0]
```

**No Sistema RET:**
```python
tipos_ativos = [
    tipo
    for tipo, checkbox in self.tipos_encargo.items()
    if checkbox.get()
]
```

---

### 4. Dicionários e Listas

```python
# Dicionário = chave: valor
pessoa = {
    'nome': 'João',
    'idade': 30,
    'cidade': 'Recife'
}

# Acessar
print(pessoa['nome'])  # João

# Lista de dicionários
pessoas = [
    {'nome': 'João', 'idade': 30},
    {'nome': 'Maria', 'idade': 25},
]

# Loop
for p in pessoas:
    print(p['nome'])
```

**No Sistema RET:**
```python
dados = {
    'arquivo': 'ND_355.pdf',
    'tipo_encargo': 'EAT',
    'valor_total': 26524.62
}
```

---

## 🛠️ Exercícios Práticos

### Exercício 1: Mini Extrator de PDF
```python
"""
Crie um programa que:
1. Abre um PDF
2. Extrai todos os números
3. Calcula a soma
4. Exibe o resultado
"""

import pdfplumber
import re

def extrair_numeros(pdf_path):
    with pdfplumber.open(pdf_path) as pdf:
        texto = pdf.pages[0].extract_text()
        
        # Encontrar todos os números
        numeros = re.findall(r'\d+(?:\.\d+)?', texto)
        
        # Converter para float e somar
        total = sum(float(n) for n in numeros)
        
        return total

# Teste
resultado = extrair_numeros('seu_pdf.pdf')
print(f"Soma: {resultado}")
```

---

### Exercício 2: Interface Simples
```python
"""
Crie uma janela com:
1. Um campo de texto
2. Um botão
3. Quando clicar, exibe o texto digitado
"""

import customtkinter as ctk

def mostrar_texto():
    texto = entrada.get()
    label_resultado.configure(text=f"Você digitou: {texto}")

janela = ctk.CTk()
janela.geometry("400x200")

entrada = ctk.CTkEntry(janela, width=300)
entrada.pack(pady=20)

botao = ctk.CTkButton(
    janela,
    text="Mostrar",
    command=mostrar_texto
)
botao.pack(pady=10)

label_resultado = ctk.CTkLabel(janela, text="")
label_resultado.pack(pady=10)

janela.mainloop()
```

---

### Exercício 3: Salvar em Excel
```python
"""
Crie um programa que:
1. Cria lista de dados
2. Converte para DataFrame
3. Salva em Excel formatado
"""

import pandas as pd
from openpyxl import load_workbook
from openpyxl.styles import Font, PatternFill

# Dados
dados = [
    {'Nome': 'João', 'Nota': 8.5},
    {'Nome': 'Maria', 'Nota': 9.0},
    {'Nome': 'Pedro', 'Nota': 7.5},
]

# Criar DataFrame
df = pd.DataFrame(dados)

# Salvar
df.to_excel('notas.xlsx', index=False)

# Formatar
wb = load_workbook('notas.xlsx')
ws = wb.active

# Cabeçalho em azul
for cell in ws[1]:
    cell.font = Font(bold=True, color='FFFFFF')
    cell.fill = PatternFill(
        start_color='1F4788',
        fill_type='solid'
    )

wb.save('notas_formatado.xlsx')
```

---

## 📚 Recursos para Aprender Mais

### 🐍 Python Básico
- [Python.org Tutorial](https://docs.python.org/pt-br/3/tutorial/)
- [Real Python](https://realpython.com/)
- [Python Brasil](https://python.org.br/)

### 🎨 CustomTkinter
- [Documentação Oficial](https://github.com/TomSchimansky/CustomTkinter)
- [Exemplos](https://github.com/TomSchimansky/CustomTkinter/tree/master/examples)

### 📄 PDFs
- [PDFPlumber Docs](https://github.com/jsvine/pdfplumber)
- [Regex101](https://regex101.com/) - Testar regex online

### 📊 Pandas
- [Pandas Docs](https://pandas.pydata.org/docs/)
- [10 Minutes to Pandas](https://pandas.pydata.org/docs/user_guide/10min.html)

### 📈 Excel
- [OpenPyXL Docs](https://openpyxl.readthedocs.io/)
- [Tutorial OpenPyXL](https://realpython.com/openpyxl-excel-spreadsheets-python/)

### 💾 SQL
- [SQLite Tutorial](https://www.sqlitetutorial.net/)
- [SQL Zoo](https://sqlzoo.net/)

---

## ❓ FAQ - Dúvidas Comuns

### Por que usar POO (Classes)?
**R:** Classes organizam código relacionado em um só lugar. Facilitam reutilização e manutenção.

### O que é `self`?
**R:** `self` é uma referência ao próprio objeto. Permite acessar atributos e métodos da instância.

### Por que usar Regex?
**R:** Regex permite encontrar padrões complexos em texto de forma eficiente. Essencial para extração de dados.

### Pandas vs Listas?
**R:** Pandas é otimizado para grandes volumes de dados e oferece funções poderosas de análise.

### Por que SQLite?
**R:** SQLite é leve, não precisa de servidor e é perfeito para apps desktop.

---

## 🎯 Checklist de Aprendizado

- [ ] Entendi o que é uma classe
- [ ] Sei usar `__init__` e `self`
- [ ] Consigo criar uma GUI básica
- [ ] Entendo como funciona `pack()`
- [ ] Sei usar `command=` em botões
- [ ] Posso abrir e ler um PDF
- [ ] Entendo regex básico
- [ ] Consigo extrair padrões de texto
- [ ] Sei criar listas de dicionários
- [ ] Entendo Pandas DataFrame
- [ ] Posso criar banco SQLite
- [ ] Sei fazer queries SQL
- [ ] Consigo criar Excel com Python
- [ ] Sei formatar células no Excel
- [ ] Entendo o fluxo completo do sistema

---

## 🚀 Próximos Passos

Após dominar o básico:

1. **Adicione funcionalidades:**
   - Filtros por data
   - Busca por empresa
   - Gráficos no Excel

2. **Melhore a interface:**
   - Barra de progresso
   - Modo claro/escuro
   - Ícones personalizados

3. **Otimize o código:**
   - Threading para PDFs grandes
   - Cache de resultados
   - Validação de dados

4. **Aprenda mais:**
   - APIs REST
   - Banco PostgreSQL
   - Deploy de apps

---

**🎓 Bons estudos! Qualquer dúvida, consulte o código comentado!**
