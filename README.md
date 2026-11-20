# Câmara em Rede

Quem vota com quem na Câmara dos Deputados. Redes de concordância entre deputados federais
nas votações nominais, de 2003 até hoje, por ano, por legislatura e por tema.

<a href="https://colab.research.google.com/github/LucasAlegre/camara-em-rede/blob/main/camara_em_rede.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Abrir no Colab"/></a>

Cada ponto é um deputado. Dois deputados ficam ligados quando votaram juntos mais do que o
esperado por acaso, segundo um modelo nulo que embaralha os votos de cada votação. Os blocos
são detectados com o algoritmo de Leiden. A visualização é uma página HTML autocontida
(Sigma.js + Graphology + ForceAtlas2) com:
- linha do tempo por ano ou legislatura;
- filtro por tema;
- lista de votações que colore os deputados pelo voto;
- composição dos blocos por partido.

A matemática completa está na página **Sobre o método** (link no rodapé da visualização,
texto em [`sobre.html`](sobre.html)).

## Como gerar

```bash
pip install -r requirements.txt
jupyter notebook camara_em_rede.ipynb   # rode todas as células
```

O notebook baixa os dados abertos da Câmara para `data/` (só na primeira vez; ~1 GB) e grava
`camara.html`, que abre em qualquer navegador. Leva alguns minutos. No Colab, o próprio
notebook baixa o `graph_viz.py` e o `sobre.html` deste repositório.

Os parâmetros ficam no início do notebook (escalas de tempo, temas, densidade de ligações, FDR).

## Arquivos

| Arquivo | Conteúdo |
|---|---|
| `camara_em_rede.ipynb` | dados → grafos (concordância, significância, comunidades) → visualização |
| `graph_viz.py` | gera a página HTML interativa a partir de grafos do igraph |
| `sobre.html` | texto da página "Sobre o método" |
| `data/logo_colors.json` | cache das cores extraídas dos logos dos partidos |

## Dados

[Dados Abertos da Câmara dos Deputados](https://dadosabertos.camara.leg.br/): arquivos anuais
`votacoesVotos`, `votacoes`, `votacoesProposicoes` e `proposicoesTemas`, e a API de partidos.
Só entram votações nominais. Antes de 2020, as votações de comissões não têm o voto de cada
deputado nos dados abertos, então até 2019 a série reflete basicamente o Plenário.

## Autor

[Lucas Alegre](https://github.com/LucasAlegre)
