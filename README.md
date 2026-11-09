# Sistema de Energia da Colonia Aurora Siger

Este projeto simula o controle de energia de uma colonia. O codigo foi mantido simples e usa os assuntos estudados: `while`, `for`, `if`, `else` e funcoes criadas com `def`. Tambem usa listas e dicionarios para guardar os dados.

## Como executar

1. Instale o Python.
2. Abra um terminal na pasta do projeto.
3. Execute:

```bash
python main.py
```

O programa pede a velocidade do vento, a geracao solar e informa se ha tempestade de areia. Para repetir a simulacao, digite `s` ao final.

## Como os dados estao organizados

O dicionario `colonia` agrupa os dados em tres partes:

- `energia`: geracao solar, geracao eolica e reserva da bateria;
- `clima`: velocidade do vento e tempestade de areia;
- `modulos`: consumo, estado e prioridade dos equipamentos.

As listas `ventos_historicos` e `geracao_historica` guardam pares de dados usados na previsao eolica.

## Regras de decisao

- Se a geracao ficar abaixo de 30, o sistema mostra um alerta critico e ativa o modo economia.
- Se a geracao ficar abaixo de 50, o sistema mostra um alerta e desliga os modulos nao essenciais.
- Habitacao/suporte de vida e suporte medico sao mantidos ligados.
- Se o consumo ainda superar a geracao, o sistema tenta usar a reserva da bateria.
- Se a geracao superar o consumo, o sistema tenta guardar o excedente sem ultrapassar a capacidade da bateria.
- Se houver tempestade de areia, a simulacao considera a geracao solar pela metade. Esse valor e uma hipotese didatica.

## Previsao de geracao eolica

O historico usado e:

- Vento: `[8, 10, 12]`
- Geracao eolica: `[20, 25, 30]`

A funcao `prever_energia_eolica()` percorre as listas com `for`, calcula uma reta simples de regressao e estima a geracao. Com vento igual a 11, a previsao e 27,5 unidades.

## Exemplo de entrada e saida

Entradas:

```text
Velocidade do vento: 11
Geracao solar: 20
Tempestade de areia: n
```

Principais resultados:

```text
Previsao de geracao eolica: 27.5
Geracao total: 47.5
Consumo inicial: 80
ALERTA: geracao abaixo de 50. Reduzindo consumo.
Consumo depois das decisoes: 35
SUGESTAO: armazenar energia excedente de 12.5
Reserva final: 112.5
```

Os numeros sao simulados para fins didaticos e nao representam medições reais.# sistema_integrado_inteligente_colonia
