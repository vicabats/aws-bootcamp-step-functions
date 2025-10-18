# aws-bootcamp-step-functions
Repositório com anotações referentes ao gerenciamento de workflows automatizados com AWS Step Function, conteúdo aprendido no curso Santander Code Girls 

# 🚀 Explorando Workflows Automatizados com AWS Step Functions

Repositório criado para documentar o desafio **"Explorando Workflows Automatizados com AWS Step Functions"** da DIO.

---

## 🧠 Objetivo

Consolidar os conhecimentos sobre **criação e execução de workflows automatizados** utilizando o serviço **AWS Step Functions**, integrando com funções Lambda e outros recursos da AWS.

---

## 🏗️ Conceitos Principais Aprendidos

- O que são **Step Functions** e como elas permitem orquestrar serviços da AWS.
- Diferença entre **State Machines**, **Tasks** e **States**.
- Integração com **AWS Lambda**.
- Utilização de **validações**, **condições** e **mapeamentos**.
- Benefícios do uso de **workflows automatizados** em aplicações serverless.

---

## ⚙️ Passo a Passo do Projeto

### 1. Criação das Funções Lambda
- Função 1: Receber e validar entrada do usuário.
- Função 2: Processar dados e retornar um resultado.
- Função 3: Armazenar saída em um bucket S3 (opcional).

### 2. Criação da State Machine no AWS Step Functions
- Definição do fluxo no formato JSON.
- Integração com as funções Lambda criadas.
- Uso de **Catch** e **Retry** para tratamento de erros.

### 3. Execução e Testes
- Execução manual pelo console da AWS.
- Testes com diferentes payloads de entrada.
- Verificação de logs no CloudWatch.

---

## 🧩 Exemplo de Definição da State Machine

```json
{
  "Comment": "Exemplo de workflow simples",
  "StartAt": "ValidaEntrada",
  "States": {
    "ValidaEntrada": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:us-east-1:123456789012:function:ValidaEntrada",
      "Next": "ProcessaDados"
    },
    "ProcessaDados": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:us-east-1:123456789012:function:ProcessaDados",
      "End": true
    }
  }
}
