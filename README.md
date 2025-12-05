# 🍽️ Sabor Express - Gerenciador de Restaurantes

## 📖 Descrição

Sabor Express é uma aplicação de console em Python que demonstra conceitos fundamentais de programação, incluindo:

- ✅ **Condicionais e Laços de Repetição** - Controle de fluxo da aplicação
- ✅ **Blocos Try-Except** - Tratamento robusto de erros
- ✅ **Funções** - Organização modular do código
- ✅ **Listas e Dicionários** - Estruturas de dados para armazenar restaurantes
- ✅ **Menu Interativo** - Navegação com validação

---

## 🎯 Funcionalidades

### 1️⃣ Cadastrar Restaurante
- Obtém nome e categoria do restaurante
- **Validações:**
  - Verifica se nome está vazio
  - Verifica se categoria está vazia
  - Verifica duplicação (mesmo nome já existe?)
- **Tratamento de erros:** Try-except para KeyboardInterrupt e exceções genéricas
- **Resultado:** Adiciona novo restaurante à lista com ID automático

### 2️⃣ Listar Restaurantes
- Exibe tabela formatada de todos os restaurantes
- Mostra: ID, Nome, Categoria, Status (Ativo/Desativado)
- **Loop:** Percorre lista e exibe cada restaurante
- **Condicional:** Mostra ícone diferente por status

### 3️⃣ Ativar/Desativar Restaurante
- Solicita ID do restaurante
- **Loop + Condicional:** Busca restaurante por ID
- Alterna status entre Ativo (True) e Desativado (False)
- **Validação:** Verifica se ID existe na lista
- **Try-Except:** Trata entrada inválida

### 4️⃣ Sair
- Encerra a aplicação com mensagem de despedida

---

## 🏗️ Estrutura do Projeto

```
sabor-express/
├── app.py                 # Aplicação principal
├── IMPROVEMENTS.md        # Documentação técnica de melhorias
└── README.md             # Este arquivo
```

---

## 🗂️ Estrutura de Dados

### Restaurante (Dicionário)
```python
{
    'id': 1,
    'nome': 'Oue Sushi',
    'categoria': 'Comida Japonesa',
    'status': False
}
```

### Lista Global
```python
restaurantes = [
    {...},  # Restaurante 1
    {...},  # Restaurante 2
    {...}   # Restaurante 3
]
```

---

## 💻 Como Usar

### Executar a Aplicação
```bash
python app.py
```

### Navegação do Menu
```
╔════════════════════════════════════════╗
║      MENU PRINCIPAL - SABOR EXPRESS    ║
╠════════════════════════════════════════╣
║ 1 - Cadastrar Restaurante              ║
║ 2 - Listar Restaurantes                ║
║ 3 - Ativar/Desativar Restaurante       ║
║ 4 - Sair                               ║
╚════════════════════════════════════════╝

Escolha uma opção (1-4): _
```

---

## 🔍 Exemplos de Uso

### Exemplo 1: Cadastrar Restaurante
```
Opção: 1

Digite o nome do restaurante: Burguer King
Digite a categoria para Burguer King: Fastfood

✅ Restaurante cadastrado com sucesso!
   ID: 4 | Nome: Burguer King | Categoria: Fastfood
```

### Exemplo 2: Validação - Nome Vazio
```
Opção: 1

Digite o nome do restaurante: 
❌ O nome do restaurante não pode estar vazio!

Pressione tecla para voltar...
```

### Exemplo 3: Validação - Duplicação
```
Opção: 1

Digite o nome do restaurante: Oue Sushi
❌ O restaurante 'Oue Sushi' já foi cadastrado!

Pressione tecla para voltar...
```

### Exemplo 4: Listar Restaurantes
```
Opção: 2

─────────────────────────────────────────────────────────────────────────────────
ID   NOME                          CATEGORIA                      STATUS
─────────────────────────────────────────────────────────────────────────────────
1    Oue Sushi                     Comida Japonesa                ❌ Desativado
2    San Pietro Pizzaria           Comida Italiana                ✅ Ativo
3    Pão com Carne                 Hamburgueria                   ❌ Desativado
─────────────────────────────────────────────────────────────────────────────────
```

### Exemplo 5: Alternar Status
```
Opção: 3

Digite o ID do restaurante: 1

✅ Restaurante 'Oue Sushi' foi Ativado!
   Status: ✅ Ativo

Pressione tecla para voltar...
```

---

## 🛡️ Tratamento de Erros

### Try-Except Implementado

#### 1. **Opção do Menu**
```python
try:
    opcao_escolhida = int(opcao_str)  # ValueError se não é número
except ValueError:
    print("\n ❌ Entrada inválida! Digite apenas números.")
```

#### 2. **Cadastro de Restaurante**
```python
try:
    nome_restaurante = input(...)
    # ... lógica
except KeyboardInterrupt:
    print("\n ⚠️  Cadastro cancelado pelo usuário.")
except Exception as e:
    print(f"\n ❌ Erro: {e}")
```

#### 3. **Alternar Status**
```python
try:
    id_restaurante = int(id_str)  # ValueError se inválido
except ValueError:
    print("\n ❌ ID inválido!")
```

---

## 📊 Conceitos de Programação

### Condicionais (if/else)
```python
if not nome_restaurante:
    print("\n ❌ Nome não pode estar vazio!")
    return
    
if restaurante_existe:
    print(f"\n ❌ Restaurante já cadastrado!")
    return

if restaurante.get('status'):
    status = "✅ Ativo"
else:
    status = "❌ Desativado"
```

### Laços de Repetição (for)
```python
# Buscar duplicação
for restaurante in restaurantes:
    if restaurante.get('nome').lower() == nome_restaurante.lower():
        restaurante_existe = True
        break

# Listar todos
for restaurante in restaurantes:
    print(f"- {restaurante.get('nome')}")

# Encontrar por ID
for restaurante in restaurantes:
    if restaurante.get('id') == id_restaurante:
        restaurante['status'] = not restaurante.get('status')
        break
```

### Match-Case (Python 3.10+)
```python
match opcao_escolhida:
    case 1:
        cadastrar_novo_restaurante()
    case 2: 
        listar_restaurantes()
    case 3: 
        alternar_status()
    case 4: 
        finalizar_app()
```

### Dicionários
```python
dados_restaurante = {
    'id': novo_id,
    'nome': nome_restaurante,
    'categoria': categoria,
    'status': False
}

restaurante.get('nome')      # Acessar com segurança
restaurante['status']        # Acessar diretamente
restaurante['status'] = True # Modificar valor
```

---

## 🎓 Objetivos de Aprendizado

Este projeto foi desenvolvido para ensinar:

1. **Fluxo de Execução** - Como a aplicação flui através de condicionais e loops
2. **Tratamento de Exceções** - Como usar try-except para evitar crashes
3. **Estruturas de Dados** - Uso de listas e dicionários
4. **Validação de Entrada** - Garantir dados corretos do usuário
5. **Modularização** - Separar código em funções reutilizáveis
6. **Menu Interativo** - Criar interfaces de usuário responsivas


## 📝 Requisitos

- Python 3.10+ (para usar match-case)
- Sistema Operacional: Windows, Linux ou macOS

## 📚 Referências

- [Python Docs - Try/Except](https://docs.python.org/3/tutorial/errors.html)
- [Python Docs - Loops](https://docs.python.org/3/tutorial/controlflow.html)
- [Python Docs - Dicionários](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)
- [Python Docs - Funções](https://docs.python.org/3/tutorial/controlflow.html#defining-functions)
