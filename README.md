# Controlador de polarização MZM com CM5 e RP2040

Projeto 3 · revisão R6 · entrada de 15 V com conector de duas vias.

Placa-base com Raspberry Pi Compute Module 5 e Raspberry Pi Pico para aquisição do sinal de um fotodiodo, geração de três saídas de polarização e supervisão do sistema. O repositório reúne os arquivos nativos do Altium, os circuitos de simulação, os relatórios e a montagem tridimensional da bancada óptica.

![Montagem tridimensional da placa](docs/imagens/montagem_3d.png)

## Autores

- Carlos Renan Correia Fidelis
- Carlos Elias Fialho de Lima
- Pablo Daniel Nascimento Vieira

Universidade Federal de Campina Grande · Engenharia Elétrica · 2026.

## Organização

| Pasta | Conteúdo |
| --- | --- |
| [hardware/altium](hardware/altium) | Projeto, 17 esquemáticos, PCB, biblioteca, BOM, conectividade e modelos 3D |
| [simulacoes/LTspice](simulacoes/LTspice) | Quatorze circuitos visuais `.asc`, netlists `.cir` e símbolos `.asy` |
| [simulacoes/modelos](simulacoes/modelos) | Macromodelos dos amplificadores e blocos funcionais |
| [docs/relatorios](docs/relatorios) | Relatório de arquitetura e relatório de simulações em Word |
| [docs/verificacao](docs/verificacao) | Registros de integridade, geometria e correção das regras |
| [docs/imagens](docs/imagens) | Vistas de montagem, interfaces e bancada |
| [docs/modelos_referencia](docs/modelos_referencia) | Modelo detalhado do CM5 utilizado na documentação |
| [media](media) | Animação de 1 min 34 s da montagem e da bancada com MZM |

## Abrir o projeto

1. Baixe o repositório por **Code → Download ZIP** e extraia todas as pastas.
2. No Altium Designer, abra [`CM5_Projeto3_R6.PrjPcb`](hardware/altium/CM5_Projeto3_R6.PrjPcb).
3. Abra `CM5_Projeto3_R6.PcbDoc` para o layout. As teclas **2** e **3** alternam as vistas 2D e 3D.
4. A biblioteca `CM5_Projeto_R6.PcbLib` acompanha o projeto. Os arquivos de modelos permanecem em suas subpastas relativas.

## Interfaces principais

| Interface | Função |
| --- | --- |
| J200 | Alimentação externa: pino 1 = +15 V; pino 2 = GND |
| J500 | Entrada de corrente do fotodiodo; centro = sinal, blindagem = GND |
| J700 / J800 / J900 | Saídas BIAS I / Q / PHI |
| TP500 / TP501 | TIA e sinal filtrado destinado ao ADC |
| TP700 / TP701 | Canal I antes e depois do relé; Q e PHI seguem a numeração 800 e 900 |

A entrada fotodetectora utiliza transimpedância nominal de 220 kΩ. O driver tem ganho nominal de 6,34 em relação à diferença entre o comando do DAC e 1,25 V. A resistência de 220 Ω na saída faz a tensão depender da carga conectada. A documentação distingue o monitor lento do controlador e a detecção rápida do sinal óptico.

## Simulações

Abra um arquivo `.asc` em `simulacoes/LTspice` e execute **Run**. Mantenha os símbolos `.asy` na mesma pasta e a pasta `modelos` ao lado de `LTspice`. As netlists `.cir` permitem inspecionar as equações e os estímulos.

O [roteiro dos quatorze ensaios](simulacoes/README.md) relaciona cada circuito às grandezas observadas. Os gráficos e suas análises estão no [relatório LTspice](docs/relatorios/Relatorio_LTspice_CM5_RP2040_MZM_R6.docx).



## Documentação e montagem

- [Arquitetura e bancada em 2D e 3D](docs/relatorios/Relatorio_CM5_RP2040_MZM_ABNT_R6.docx)
- [Circuitos e resultados no LTspice](docs/relatorios/Relatorio_LTspice_CM5_RP2040_MZM_R6.docx)
- [Vídeo da montagem e da bancada](media/CM5_R6_Trailer_Bancada.mp4)

Os relatórios apresentam resultados de CAD, cálculos nominais e simulações. O MZM do ensaio óptico é um modelo ideal em malha aberta com parâmetros declarados. As cenas 3D são representações de montagem. A origem dos recursos de terceiros está registrada em [THIRD_PARTY.md](THIRD_PARTY.md).
