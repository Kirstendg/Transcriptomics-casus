# De door transcriptomics geïdentificeerde genen: ANKRD30BL, MT-ND6 & SLC9A3R2 geven mogelijk meer inzicht in de ziekteprocessen van Reumatoïde Artritis (RA)

## Inhoudsopgave
1. Introductie
2. Methode
3. Resultaten
4. Conclusie

## 1. Introductie
Reumatoïde Artritis (RA) is een chronische auto-immuunziekte dat pijn, irritatie en inflammatie van de gewrichten veroorzaakt (Fig 1) (Chauhan et al., 2023). Wereldwijd wordt ongeveer 0,5% van mensen beïnvloed door RA (Deseatnicova et al., 2026). RA ontstaat door een combinatie van genetische en omgevingsfactoren waarbij roken een bekende risicofactor is. Een recente studie heeft een toename gevonden van RA-diagnoses over een periode van 32 jaar, van 11,66 naar 13,48 per 100,000 mensen (Zhang et al., 2025). 
Langdurige onbehandelde RA kan lijden tot gewrichtsmisvormingen, functieverlies, en erosie van kraakbeen en bot (Wang et al., 2019). Daarom is een vroegtijdige diagnose van groot belang. Hoewel er momenteel geen genezend medicijn bestaat, kan RA door medicatie en patiënten educatie worden geremd (Majithia & Geraci, 2007). Voor de ontwikkeling van nieuwe medicijnen kan transcriptomics een belangrijke rol spelen, omdat hiermee zichtbaar wordt welke genen en pathways differentieel tot expressie komen bij patiënten met RA in vergelijking met gezonde individuen. Deze inzichten kunnen bijdragen aan het begrijpen van het ontstaan en de progressie van de ziekte.


<img width="632" height="632" alt="RA plaatje" src="https://github.com/user-attachments/assets/ee521a74-b11b-472b-844a-8541c6312540" />

`Figuur 1; Weergave van Reumatoïde Artitis in een hand.`

## 2. Methode
De gebruikte data is afkomstig uit een eerder onderzoek (Platzer et al., 2019). Het humane referentiegenoom werd geïndexeerd met Rsubread versie 2.14.2 en de reads daarop gemapt (fig. 2) (Shi, 2022). Dit volgens standaardinstellingen van Rsubread. Resulterend zijn BAM bestanden. Met het GTF bestand GCF_000001405.40 werden reads per gen gekwantificeerd. Met DESeq2 versie 1.40.2 werd een count matrix geconstrueerd en differentiële genexpressie bepaald (Package “DESeq2,” 2025). Significante genen voldeden aan padj < 0,05. Voor visualisatie en functionele interpretatie zijn drie analyses uitgevoerd: een Volcano plot om opvallende genen te selecteren op basis van log2 fold change en bijgestelde p waarde, een KEGG padverrijkingsanalyse op HSA05323, gevisualiseerd met Pathview versie 1.40.0, om betrokken moleculaire routes te identificeren, en een Gene Ontology (GO) enrichmentanalyse, dit op basis van de laagste BH gecorrigeerde over-representatie p-waarden (Bioconductor - EnhancedVolcano, n.d.; Gene Ontology Enrichment Analysis, n.d.; Title Client-Side REST Access to the Kyoto Encyclopedia of Genes and Genomes (KEGG), 2025; Maintainer & Luo, 2025). Bij GO enrichment lengtebias gecorrigeerd met goseq versie 1.52.0 en gebruikten org.Hs.eg.db versie 3.17.0 voor annotatie (hg19, geneSymbol) (Bioconductor - Goseq, n.d.; Bioconductor - Org.Hs.Eg.Db, n.d.). Overrepresentatietests werden gecorrigeerd met de Benjamini–Hochberg methode. Alle gebruikte R pakketten en versies zijn gedocumenteerd in het bijgevoegde R script.

<img width="2636" height="632" alt="Flowchart transcriptomics casus RA" src="https://github.com/user-attachments/assets/d8382976-e858-4706-973e-79095677d853" />

`Figuur 2; Flowchart gemaakt met Lucidchart (Diagram Software | Lucidchart, n.d.). Synoviumbiopt is uitgevoerd op vier patiënten met RA en vier gezonde patiënten. Hieruit is DNA geïsoleerd en RNA sequencing uitgevoerd om RNA-seq-data te verkrijgen. Hiernaast is het humane referentie genoom verkregen via de NCBI databank, waarna deze is geïndexeerd (National Center for Biotechnology Information, n.d.). Samples zijn gemapt tegen het geïndexeerde genoom. Reads per gen kwantificeert met BAM-files van alle patiënten en het humane GTF-file. Count matrix is gemaakt en vervolgens statistische analyses uitgevoerd (KEGG pathway, Volcano plot en GO analyse).`

[Rsubread handleiding](https://subread.sourceforge.net/SubreadUsersGuide.pdf).

`Tabel 1; MetaData van de verkregen data van het eerder uitgevoerde onderzoek.`


| Patiënt | Leeftijd | Geslacht | Ziek of gezond | 
| ------- | -------- | -------- | -------------- |
| SRR4785819 | 31 | Female | Normal | 
| SRR4785820 | 15 | Female | Normal |
| SRR4785828 | 31 | Female | Normal |
| SRR4785831 | 42 | Female | Normal |
| SRR4785979 | 54 | Female | Rheumatoid arthritis (established) |
| SRR4758980 | 66 | Female | Rheumatoid arthritis (established) |
| SRR4785986 | 60 | Female | Rheumatoid arthritis (established) |
| SRR4785988 | 59 | Female | Rheumatoid arthritis (established) |



## 3. Resultaten
Differentiële genexpressie is uitgevoerd met DESeq2, hieruit volgde data van 29407 genen. Dit in verhouding van patiënten met RA en gezond. Voor visualisatie en het KEGG pathway is een Log2 fold change van 1 en gecorrigeerde p-waarde van 0,05 aangehouden, zie R script. Dit resulteerde in 2085 significante omhoog gereguleerde genen en 2487 omlaag gereguleerde genen.

Volcano plot is gebruikt voor de visualisatie van de differentiële genexpressie. Rood geeft up regulatie aan en groen down regulatie, zie figuur 3. Grijs heeft geen significante genexpressie. Zichtbaar zijn ANKRD30BL, MT-ND6 en SLC9AR2 zeer significante up regulatie mogelijk betrokken bij zichtbeeld van RA, zie figuur 3.

De GO-analyse liet zien dat de tien meest significante gereguleerde genen betrokken zijn bij: chronische immuun activatie, versterkte signaalroutes, metabolisme, eiwit binding onderandere receptoren, oxidatieve stress, verhoogde cytokineproductie, inflammasomen en antigeen presentatie, zie figuur 4 en tabel https://github.com/Kirstendg/Transcriptomics-casus/blob/main/Resultaten/GO_analyse.xlsx. Dit zijn allemaal bekende symptomen bij RA. 

KEGG pathway met pathview is gebruikt voor visualisatie van de betrokken eiwitten bij immuun responses met RA. Verhoogde expressie van IL6, IL1β en onder andere IL8 geeft inflammatie van de gewrichten, zie figuur 4. Verder is MMP1/3 verhoogd wat gewricht destructie kan zorgen, zie figuur 5.

<img width="632" height="632" alt="Correcte Volcanoplot2" src="https://github.com/user-attachments/assets/8b3924f8-55a8-4c68-8f7b-fe303e977dbb" />

`Figuur 3; Volcano plot van differentiële genexpressie gemaakt met behulp van het EnhancedVolcano package in R-studio. Dit op basis van 29407 variabelen. Weergegeven op de x-as is de Log2 fold change en op de y-as -log10 P. Hierbij zijn de drempels en geselecteerde genlabels zichtbaar. De grijs gekleurde genen hebben geen statisch significante differentiële genexpressie. De rood gekleurde genen hebben een hoge statistische significantie en zijn sterk verhoogd. Alle groen gekleurde genen zijn niet statistisch relevant volgens de gestelde eisen.`

<img width="738" height="341" alt="GO analyse plot" src="https://github.com/user-attachments/assets/8e66ff42-615c-43fa-9028-b63aea5c0502" />

`Figuur 4; Puntdiagram van de uitgevoerde GO-enrichment resultaten. Zichtbaar op de x-as is het percentage Hits van de gedetecteerde top 10 gen ID’s per GO-term. Aangegeven op de y-as staan de GO-termen, hierbij is de grootte van de punten in samenhang met het aantal genen. De kleur van ieder punt is de p-waarde, hoe donkerder hoe significanter. Hoe hoger een GO-term hoe significanter deze tot expressie komt.`

<img width="1492" height="632" alt="Correcte pathview" src="https://github.com/user-attachments/assets/3e24040c-4504-4d3d-b974-85c7d4e2fb47" />

`Figuur 5; KEGG pathway voor Reumatoïde Artitis (RA) gerendeerd met Pathview package in R-studio. Zichtbaar zijn alle betrokken eiwitten en enzymen bij RA. Bij een verhoogde differentiële expressie, zie IL6, ILS of MMP1/3, zijn de eiwitten en enzymen rood gekleurd. Bij een verlaagde differentiële expressie, zie VEGF, API en IL17, zijn de eiwitten en enzymen groen gekleurd. Bij geen verschil grijs.`


## 4. Conclusie
Reumatoïde Artritis (RA) is een chronische auto-immuunziekte dat pijn, irritatie en ontsteking van de gewrichten veroorzaakt, er is nog geen genezing (Chauhan et al., 2023). Transcriptomics kan hier een waardevolle bijdrage aanleveren. In dit onderzoek zijn biopten genomen van vier patiënten met RA en vier gezonde controles. Nadat het aantal genen was gekwantificeerd, zijn drie statistische analyses uitgevoerd om inzicht te geven in de ziekteprocessen van RA.

Uit analyse zijn 29407 genen geïdentificeerd, waarvan 2085 significant omhoog en 2487 significant omlaag gereguleerd waren. Na visualisatie met Volcano-plot zijn ANKRD30BL, MT-ND6 & SLC9A3R2 benadrukt met mogelijke bijdragen aan RA. KEGG- en GO-analyse tonen versterkte immuunresponsen en ontstekingsroutes, met verhoogde expressie van cytokinen IL6, IL1β en IL8 (Alturaiki et al., 2022). Verder is MMP1/3 geassocieerd met schade aan gewrichten (Green et al., 2003). De top tien gevisualiseerde GO-termen komen overeen met bekende mechanismen van RA.

De gekozen drempels voor log2 fold change en padj kunnen het aantal significante genen beïnvloeden. Verdere bijdrage aan de validiteit van de gegevens is de steekproef grootte. Door het beperkte aantal samples kan de relevantie van de gevonden verschillen ter discussie staan. Daarom wordt aanbevolen de steekproef te vergroten en variatie in drempelkeuzes te onderzoeken.