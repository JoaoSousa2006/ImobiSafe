# ImobiSafe

## Aprendizagem de Máquina
### Professor Bruno Zolotareff
### Giulia Gomes Grossi
### João Victor de Sousa

# Projeto: Perfis de Criminalidade dos Municípios Paulistas
**MVP — Google Colab | Escopo definido**

## Objetivo e problema
Agrupar os municípios do Estado de São Paulo por semelhança no perfil de criminalidade, usando indicadores públicos agregados e o algoritmo **K-Means**.

- **Região:** Estado de São Paulo.
- **Unidade geográfica:** município, identificado preferencialmente pelo código IBGE.
- **Objetivo do MVP:** descobrir grupos com padrões semelhantes de ocorrências, não classificar municípios como “seguros” ou “perigosos”.
- **Fora do escopo desta versão:** previsão de preços imobiliários. Pode ser uma etapa futura independente.

A primeira execução com dados fictícios serve apenas para testar o código. A análise só poderá ser considerada baseada em dados reais depois que os arquivos oficiais forem baixados, mapeados e validados.


## Referências iniciais

1. **SSP-SP — Estatísticas criminais e dados abertos (fonte principal para São Paulo).** O portal publica séries municipais; confira ano, unidade e dicionário de cada arquivo.
   https://www.ssp.sp.gov.br/estatistica/consultas
   https://www.ssp.sp.gov.br/transparencia/dados-abertos
2. **IBGE — Estimativas da população residente.** Usar o ano compatível com a janela criminal.
   https://www.ibge.gov.br/estatisticas/sociais/populacao/9103-estimativas-de-populacao.html
3. **MJSP/SINESP — Dados nacionais de segurança pública.** Fonte complementar para validação; conferir cobertura e definições municipais.
   https://dados.mj.gov.br/dataset/sistema-nacional-de-estatisticas-de-seguranca-publica

**Decisão do MVP:** priorizar SSP-SP, pois o escopo é o Estado de São Paulo. SINESP fica como fonte complementar; não misturar indicadores de fontes diferentes sem confirmar definições e cobertura.


## Solução proposta

1. Baixar um arquivo oficial da SSP-SP com ocorrências por município e ano (ou dados mensais de um ano completo).
2. Consultar a população do IBGE para o mesmo ano e relacionar municípios pelo código IBGE; se a fonte criminal trouxer apenas nomes, normalizar e revisar correspondências.
3. Validar período, definições, duplicidades, valores ausentes e cobertura dos municípios.
4. Calcular taxas por 1.000 habitantes, padronizar as variáveis e aplicar K-Means. Testar mais de um valor de k e descrever os clusters pelas taxas médias.
5. Usar Make para detectar/arquivar atualizações, validar arquivos e guardar metadados e versões.
6. Na fase inicial, executar o Colab manualmente. Colab comum não é um serviço permanente; automação integral exige execução persistente ou sob demanda.

**Fora do MVP atual:** previsão de preços imobiliários. Primeiro validar o agrupamento com dados criminais reais.
