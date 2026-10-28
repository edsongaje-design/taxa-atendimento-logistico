# Taxa de Atendimento Logístico (SLA / OTIF)

Planilha Excel com macros (VBA) para **lançar mensalmente a taxa de atendimento logístico por montadora**, guardar a **evidência** de cada taxa e acompanhar tudo num **painel com farol**, linha de meta, tendência e mapa de calor.

![Painel de demonstração](docs/demo.png)

> Os números do arquivo `_DEMO` são **fictícios**, criados só para demonstração.

## O que ela faz

- **Lançamento simples:** uma linha por montadora e uma coluna por mês. Só a taxa é digitada, e a planilha aceita valores de 0% a 100%.
- **Farol automático:** verde, laranja e vermelho conforme limites que você define (padrão: verde ≥ 95%, laranja ≥ 90% e < 95%, vermelho < 90%).
- **Evidências:** o botão *Colar evidência* guarda o print do portal ou relatório ao lado do mês, com usuário e data/hora. Você digita o valor que aparece no print e a planilha confere se bate com o lançamento (✔ Confere / ⚠ Divergente).
- **Painel executivo:**
  - cartões de resumo (média geral, quantas montadoras estão no verde, maior e menor média, taxas sem evidência);
  - mapa de calor montadora × mês;
  - um gráfico por montadora, com colunas coloridas pelo farol, linha de meta tracejada e tendência (média móvel de 3 meses).
- **Fácil de crescer:** o botão *Adicionar montadora* cria a linha, o gráfico e a linha do mapa de calor.
- **Virada de ano:** o botão *Novo ano* salva uma cópia do ano atual e limpa os lançamentos e as evidências.
- **Impressão pronta:** a aba Gráficos imprime em 2 páginas, resumo e mapa de calor na primeira, gráficos na segunda.

## Estrutura do repositório

```
├── README.md
├── Taxa_Atendimento_Logistico.xlsx        # modelo vazio, para usar
├── Taxa_Atendimento_Logistico_DEMO.xlsx   # exemplo com dados fictícios
├── vba/
│   └── modTaxaAtendimento.bas             # código VBA (módulo único)
└── docs/
    └── demo.png                           # imagem do painel
```
## Como instalar

Requer **Excel para Windows** com permissão para executar macros.

1. Baixe `Taxa_Atendimento_Logistico.xlsx` e `vba/modTaxaAtendimento.bas`. Baixe o `.bas` pelo botão **Download raw file**, sem copiar e colar o texto.
2. Abra a planilha no Excel e aperte **Alt + F11** para abrir o editor do VBA.
3. Vá em **Arquivo → Importar arquivo...** e escolha o `modTaxaAtendimento.bas`.
4. No editor, abra o módulo importado, clique dentro da rotina `ConfigurarPlanilha` e aperte **F5**. Isso cria os botões e os gráficos.
5. Salve como **Pasta de Trabalho Habilitada para Macro do Excel (.xlsm)**.

Se o Excel bloquear as macros porque o arquivo veio da internet, clique com o botão direito no arquivo, abra **Propriedades** e marque **Desbloquear**.

> **Atenção à codificação:** o `.bas` está em Windows-1252 (padrão do VBA em português). Se você copiar o código para outro arquivo e salvar em UTF-8, as letras acentuadas serão corrompidas e a importação poderá falhar. Mantenha o arquivo original.

## Como usar

1. Na aba **Lançamento**, escolha o ano em `B3` e digite a taxa de cada mês (ex.: `98,4` vira 98,4%).
2. Copie o print da evidência (por exemplo, **Win + Shift + S**), clique na célula do mês e use **Colar evidência**. Depois digite, na aba Evidências, o valor que aparece no print.
3. Abra a aba **Gráficos** para ver o painel, que se atualiza sozinho.

### Ajustes

| Onde | O que controla |
|---|---|
| `Lançamento!H3` | Limite do verde (padrão 95%) |
| `Lançamento!K3` | Limite do laranja (padrão 90%) |
| `Lançamento!N3` | Onde o eixo dos gráficos começa (padrão 0%); aplique com *Atualizar gráficos* |
| Coluna **META** | Meta de cada montadora (padrão 100%) |

### Botões

| Botão | Função |
|---|---|
| Colar evidência | Registra o print do mês selecionado |
| Ver evidência | Vai até a evidência do mês selecionado |
| Adicionar montadora | Inclui uma nova montadora na planilha e no painel |
| Atualizar gráficos | Recria os gráficos (use depois de mudar o eixo em `N3`) |
| Novo ano | Salva uma cópia do ano e limpa a planilha para o ano seguinte |
## Limites

- Até **30 montadoras** (o mapa de calor mostra até **16**).
- Até **400 evidências** por ano.
- Um ano por arquivo; use *Novo ano* para virar o ano.
- Desenvolvido para Excel no Windows.

## Aviso

Esta planilha é um modelo. **Não publique dados reais, prints de portais de clientes ou caminhos de arquivos da sua empresa.** Use o arquivo `_DEMO` como exemplo.

## Autor

_edsongaje-desing_
