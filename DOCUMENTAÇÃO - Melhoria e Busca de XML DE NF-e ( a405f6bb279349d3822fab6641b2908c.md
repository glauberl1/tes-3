# DOCUMENTAÇÃO - Melhoria e Busca de XML DE NF-e (TMSAC17 - SIGATMS)

## CONTÉUDO

- [01. VISÃO GERAL](https://tdn.totvs.com.br/pages/releaseview.action?pageId=618870156#MelhoriaBuscadeXMLdeNFe(TMSAC17SIGATMS)-01.VIS%C3%83OGERAL)
- [02. CONFIGURAÇÃO PARA IMPORTAÇÃO](https://tdn.totvs.com.br/pages/releaseview.action?pageId=618870156#MelhoriaBuscadeXMLdeNFe(TMSAC17SIGATMS)-02.CONFIGURA%C3%87%C3%83OPARAIMPORTA%C3%87%C3%83O)
- [2.1 Configuração TSS no Protheus SIGATMS](https://tdn.totvs.com.br/pages/releaseview.action?pageId=618870156#MelhoriaBuscadeXMLdeNFe(TMSAC17SIGATMS)-2.1Configura%C3%A7%C3%A3oTSSnoProtheusSIGATMS)
    - [TELA DE CONFIGURAÇÃO](https://tdn.totvs.com.br/pages/releaseview.action?pageId=618870156#MelhoriaBuscadeXMLdeNFe(TMSAC17SIGATMS)-TELADECONFIGURA%C3%87%C3%83O)
- [2.2 Schedule de Importação](https://tdn.totvs.com.br/pages/releaseview.action?pageId=618870156#MelhoriaBuscadeXMLdeNFe(TMSAC17SIGATMS)-2.2ScheduledeImporta%C3%A7%C3%A3o)
    - [CONFIGURAÇÃO - VIA JOB](https://tdn.totvs.com.br/pages/releaseview.action?pageId=618870156#MelhoriaBuscadeXMLdeNFe(TMSAC17SIGATMS)-CONFIGURA%C3%87%C3%83O-VIAJOB)
    - [PROCESSAMENTO VIA ROTINA CONFERÊNCIA DE COLETA](https://tdn.totvs.com.br/pages/releaseview.action?pageId=618870156#MelhoriaBuscadeXMLdeNFe(TMSAC17SIGATMS)-PROCESSAMENTOVIAROTINACONFER%C3%8ANCIADECOLETA)
- [03. ROTINA CONFERÊNCIA DE COLETA](https://tdn.totvs.com.br/pages/releaseview.action?pageId=618870156#MelhoriaBuscadeXMLdeNFe(TMSAC17SIGATMS)-03.ROTINACONFER%C3%8ANCIADECOLETA)
- 
- [04. GRAVAÇÃO DOS DADOS](https://tdn.totvs.com.br/pages/releaseview.action?pageId=618870156#MelhoriaBuscadeXMLdeNFe(TMSAC17SIGATMS)-04.GRAVA%C3%87%C3%83ODOSDADOS)
- [05. TABELAS UTILIZADAS](https://tdn.totvs.com.br/pages/releaseview.action?pageId=618870156#MelhoriaBuscadeXMLdeNFe(TMSAC17SIGATMS)-05.TABELASUTILIZADAS)
- [06. ASSUNTOS RELACIONADOS](https://tdn.totvs.com.br/pages/releaseview.action?pageId=618870156#MelhoriaBuscadeXMLdeNFe(TMSAC17SIGATMS)-06.ASSUNTOSRELACIONADOS)

 [01. VISÃO GERAL](https://tdn.totvs.com.br/pages/releaseview.action?pageId=618870156#MelhoriaBuscadeXMLdeNFe(TMSAC17SIGATMS)-01.VIS%C3%83OGERAL) 

Foi implementada a rotina de busca de XML completo da NF-e na SEFAZ.

Quando a NF-e for emitida contra o CNPJ da empresa, será possível baixar o XML através de consulta junto ao Órgão Validador SEFAZ, facilitando a integração com o Módulo TOTVS Logística TMS.

Sendo assim, foi disponibilizado na rotina de [Conferência de Coleta (TMSA461 - SIGATMS)](https://tdn.totvs.com/pages/viewpage.action?pageId=485877452) a visualização das chaves das NFe-s.

> **Importante:**
> 

> Estas melhorias estarão disponíveis à partir do **release 12.1.33.**
> 

## **02. CONFIGURAÇÃO PARA IMPORTAÇÃO**

## **2.1 Configuração TSS no Protheus SIGATMS**

Para importação do XML das NFe-s, será necessário efetuar a configuração dos parâmetros do TSS.

Para isso, acessar o menu Miscelânea > Simulado > CTE SEFAZ.

Na tela seguinte, escolha a opção MDFe.

![Untitled](DOCUMENTAC%CC%A7A%CC%83O%20-%20Melhoria%20e%20Busca%20de%20XML%20DE%20NF-e%20(%20a405f6bb279349d3822fab6641b2908c/Untitled.png)

Clique em Outras Ações > **Manifesto Destino.**

![Untitled](DOCUMENTAC%CC%A7A%CC%83O%20-%20Melhoria%20e%20Busca%20de%20XML%20DE%20NF-e%20(%20a405f6bb279349d3822fab6641b2908c/Untitled%201.png)

Configure o ambiente como desejado (homologação/produção) e salve o registro.

### **TELA DE CONFIGURAÇÃO**

![Untitled](DOCUMENTAC%CC%A7A%CC%83O%20-%20Melhoria%20e%20Busca%20de%20XML%20DE%20NF-e%20(%20a405f6bb279349d3822fab6641b2908c/Untitled%202.png)

## **2.2 Schedule de Importação**

Para o processamento (busca da NF-e) na SEFAZ, pode ser feito de duas maneiras. Uma delas é a configuração do Job (Schedule) através do configurador do Protheus (SIGACFG) ou através de opção manual localizada no Outras Ações da rotina [Conferência de Coleta (TMSA461 - SIGATMS)](https://tdn.totvs.com/pages/viewpage.action?pageId=485877452).

### **CONFIGURAÇÃO - VIA JOB**

Acessar o Configurador (SIGACFG), e, navegar até o menu  Ambiente > Schedule > Schedule;

Configure os campos conforme abaixo:

- Rotina: preencha com a função **TMSAC17**;
- Empresa/Filial: Selecione todas as filiais que irão executar o schedule de busca das NFes.
- Módulo: 43 - SIGATMS
- Relação a recorrência, recomendamos configurar o Job com tempo de execução maior que 5 minutos ou maior intervalo - para evitar consumo indevido.

![Untitled](DOCUMENTAC%CC%A7A%CC%83O%20-%20Melhoria%20e%20Busca%20de%20XML%20DE%20NF-e%20(%20a405f6bb279349d3822fab6641b2908c/Untitled%203.png)

### **PROCESSAMENTO VIA ROTINA CONFERÊNCIA DE COLETA**

Foi disponibilizado no Outras Ações da rotina [Conferência de Coleta (TMSA461 - SIGATMS)](https://tdn.totvs.com/pages/viewpage.action?pageId=485877452) a opção **Processa NF-e** que executará o processamento (busca da NF-e) na SEFAZ assim que for acionada.

![Untitled](DOCUMENTAC%CC%A7A%CC%83O%20-%20Melhoria%20e%20Busca%20de%20XML%20DE%20NF-e%20(%20a405f6bb279349d3822fab6641b2908c/Untitled%204.png)

## **03. ROTINA CONFERÊNCIA DE COLETA**

Com ambiente atualizado, será demonstrado ao acessar a rotina de [Conferência de Coleta (TMSA461 - SIGATMS)](https://tdn.totvs.com/pages/viewpage.action?pageId=485877452), a tabela filha (DMH) que permitirá a digitação manual ou leitura do código de barras da DANFE, armazenando-a para uma futura importação - este procedimento poderá ser utilizado **com ou sem** a integração do processo Checklist;

Esta tabela irá conter os campos de vínculo com a conferência da coleta, a chave eletrônica da DANFE, e o status que indicará que o registro já foi processado ou não **(*)** imagem abaixo.

![Untitled](DOCUMENTAC%CC%A7A%CC%83O%20-%20Melhoria%20e%20Busca%20de%20XML%20DE%20NF-e%20(%20a405f6bb279349d3822fab6641b2908c/Untitled%205.png)

## **04. GRAVAÇÃO DOS DADOS**

Quando encontrado o XML da NFe na SEFAZ, através do Job ou do processo manual, automaticamente o arquivo será gravado na pasta XMLNFE\NEW referente a importação do EDI ([Clique aqui](https://centraldeatendimento.totvs.com/hc/pt-br/articles/360026949131-MP-TMS-TMSAE80-Importa%C3%A7%C3%A3o-de-Notas-Fiscais-XML) para saber mais sobre configuração do EDI). Este arquivo ficará disponível para ser importado para a tabela DE5 (EDI - Notas Fiscais).

## **05. TABELAS UTILIZADAS**

- DMH - Conferência de NF-e

## **06. ASSUNTOS RELACIONADOS**

- [Conferência de Coleta (TMSA461 - SIGATMS)](https://tdn.totvs.com/pages/viewpage.action?pageId=485877452)
- [MP - TMS - TMSAE80 Importação de Notas Fiscais - XML](https://centraldeatendimento.totvs.com/hc/pt-br/articles/360026949131-MP-TMS-TMSAE80-Importa%C3%A7%C3%A3o-de-Notas-Fiscais-XML)

[documento_de_referencia](https://tdn.totvs.com.br/label/PROT/documento_de_referencia)[totvs_logistica_tms](https://tdn.totvs.com.br/label/PROT/totvs_logistica_tms)[linha_protheus](https://tdn.totvs.com.br/label/PROT/linha_protheus)[tms_protheus](https://tdn.totvs.com.br/label/PROT/tms_protheus)[sigatms](https://tdn.totvs.com.br/label/PROT/sigatms)[gestao_de_transporte](https://tdn.totvs.com.br/label/PROT/gestao_de_transporte)[bra](https://tdn.totvs.com.br/label/PROT/bra)[supply_ml_log_tms](https://tdn.totvs.com.br/label/PROT/supply_ml_log_tms)[versao_12](https://tdn.totvs.com.br/label/PROT/versao_12)[tmsc17](https://tdn.totvs.com.br/label/PROT/tmsc17)[busca_nfes](https://tdn.totvs.com.br/label/PROT/busca_nfes)[sefaz](https://tdn.totvs.com.br/label/PROT/sefaz)[edi](https://tdn.totvs.com.br/label/PROT/edi)[tmsa461](https://tdn.totvs.com.br/label/PROT/tmsa461)