# Guia Financeiro — Manual de Manutenção

Este documento explica como manter o site sem precisar mexer no código HTML/CSS/JS.

## Estrutura de arquivos

```
guia-financeiro/
├── guia-financeiro.html          ← o site (não precisa editar para atualizar contas)
├── data/
│   └── plano-de-contas.json      ← TODAS as contas comentadas ficam aqui
└── downloads/
    └── plano-de-contas-guia-financeiro.xlsx   ← planilha para download
```

## Como adicionar, editar ou remover uma conta

Abra `data/plano-de-contas.json` em qualquer editor de texto (Bloco de Notas, VS Code, etc.) — **não precisa saber programar**, é só respeitar o formato.

Cada conta é um bloco assim:

```json
{
  "codigo": "3.1.008",
  "titulo": "Nome da Conta",
  "categoria": "Despesa administrativa",
  "cor": "vermelho",
  "segmentos": ["comercio", "servicos", "industria"],
  "definicao": "O que é essa conta, em uma frase simples.",
  "quandoUsar": "Quando essa conta deve ser usada.",
  "quandoNaoUsar": "Situações em que essa conta NÃO deve ser usada.",
  "exemplo": "Um exemplo prático com valor em R$.",
  "observacao": "Qualquer observação extra. Use \"—\" se não houver nada a comentar."
}
```

**Para adicionar uma conta nova:**
1. Copie um bloco inteiro (do `{` ao `}`) de uma conta parecida.
2. Cole logo antes do `]` que fecha a lista (repare que precisa de uma vírgula `,` separando do bloco anterior).
3. Preencha os campos com o conteúdo da nova conta.
4. Salve o arquivo.

**Para editar uma conta:** só altere o texto entre aspas do campo desejado.

**Para remover uma conta:** apague o bloco inteiro (do `{` ao `}` correspondente, junto com a vírgula que o separa do próximo).

### Valores aceitos

- **`cor`** (define a cor do selo da categoria): `"verde"` (receita), `"amarelo"` (custo), `"vermelho"` (despesa), `"azul"` (ativo/passivo).
- **`segmentos`** (quais filtros mostram essa conta): use uma lista com um ou mais de `"comercio"`, `"servicos"`, `"industria"`. Uma conta comum aos três fica `["comercio", "servicos", "industria"]`.

### Cuidado para não quebrar o arquivo

- Todo texto fica **entre aspas duplas** `" "`.
- Cada campo termina com vírgula `,`, **exceto o último campo do bloco** (`"observacao"`), que não leva vírgula.
- Se precisar usar aspas dentro do texto, escreva `\"` no lugar de `"` (por exemplo: `"Não confundir com \"Vendas de Mercadorias\"."`)
- Depois de editar, você pode validar o arquivo colando o conteúdo em [jsonlint.com](https://jsonlint.com) para conferir se não há erro de digitação antes de publicar.

## Por que isso é mais fácil de manter

Antes, cada conta era um bloco de HTML dentro do próprio site — editar exigia mexer em código e tinha risco de quebrar o layout. Agora, o site lê os dados desse arquivo `.json` automaticamente: você só edita uma lista organizada de informações, sem tocar em HTML.

## Atenção ao nome do arquivo da logo

O arquivo `assets/sattva-logo.webp` precisa manter **esse nome exato, sempre em minúsculas**. No seu computador (Windows/Mac) isso não faz diferença, mas o GitHub Pages roda em Linux, que diferencia maiúsculas de minúsculas — se o arquivo for renomeado para `Sattva-logo.webp` ou qualquer variação de caixa, a logo quebra em produção mesmo funcionando normalmente no seu computador. Se isso acontecer, o site mostra "Sattva" em texto no lugar do ícone quebrado (fallback automático), mas o ideal é manter o nome do arquivo correto.

## Importante: como visualizar o site depois de editar

O navegador só carrega o `plano-de-contas.json` quando o site é acessado por um endereço `http://` ou `https://` (hospedado). Se você apenas clicar duas vezes no arquivo `guia-financeiro.html` no computador (abrindo como `file://`), o navegador bloqueia esse carregamento por segurança e o Plano de Contas aparece vazio, com um aviso na tela.

Isso é normal e não é um erro do site — funciona perfeitamente assim que os três itens (`guia-financeiro.html`, a pasta `data/` e a pasta `downloads/`) forem publicados juntos em qualquer hospedagem (ou até testados localmente com um servidor simples, ex.: `npx serve` na pasta, ou a extensão "Live Server" do VS Code).

## Como funcionam as contas favoritas

- Qualquer pessoa que acessa o site pode clicar na estrela (☆) de uma conta para marcá-la como favorita.
- As favoritas ficam salvas **no navegador de cada pessoa** (usando `localStorage`), não em um banco de dados compartilhado — ou seja, é uma preferência pessoal de cada usuário, e não aparece para outras pessoas nem sincroniza entre computadores/celulares diferentes.
- O botão "★ Só favoritas" filtra a visualização para mostrar apenas as contas marcadas.
- Isso não exige nenhuma manutenção da sua parte — é 100% automático no navegador do usuário.

## Atualizando a planilha Excel

O arquivo `downloads/plano-de-contas-guia-financeiro.xlsx` é independente do JSON — ele não é gerado automaticamente a partir do arquivo `.json`. Se você adicionar contas novas no site, lembre-se de atualizar a planilha manualmente (ou peça para regenerá-la a partir da mesma lista de contas) para os dois ficarem sincronizados.
