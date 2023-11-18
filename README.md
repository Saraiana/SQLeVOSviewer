# SQLeVOSviewer
Consulta SQL no BigQuery para explorações bibliográficas no VOS Viewer - programa de visualização e de análise de dados bibliométricos. 

# Consulta que retornou a lista de DOIs de trabalhos para cada programa de uma entidade (Instituição de Ensino Superior)

SELECT

  ppg_doi.CD_PROGRAMA_IES AS programa,
  
  works.doi AS doi
  
FROM

  `insyspo.publicdb_capes_ppg.ppg_doi` AS ppg_doi
  
JOIN

  `insyspo.publicdb_openalex_2023_08_rm.works` AS works
  
ON

  ppg_doi.DOI = SUBSTR(works.doi, 17)
  
JOIN

  `insyspo.publicdb_capes_ppg.ppg` AS ppg
  
ON

  ppg_doi.CD_PROGRAMA_IES = ppg.CD_PROGRAMA_IES
  
WHERE

  ppg.CD_ENTIDADE_CAPES = 53001010;
  

![image](https://github.com/Saraiana/SQLeVOSviewer/assets/102194276/6504ff5a-5f2e-4493-bc94-8b64ea1fd945)

Resultado da análise no VOSviewer, considerando a maior ocorrência de termos: 

![image](https://github.com/Saraiana/SQLeVOSviewer/assets/102194276/2de44cf3-9951-4ed1-a2ee-a1a34503a0f4)




  
