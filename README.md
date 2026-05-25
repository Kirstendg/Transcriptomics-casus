# Hier pakkende titel invoeren

# Inhoudsopgave
1. Introductie
2. Methode
3. Resultaten
4. Conclusie
5. Beheer

# 1. Introductie
Reumatoïde Artitis (RA) is een chronische auto-immuunziekte dat pijn, irritatie en inflammatie van de gewrichten veroorzaakt (Chauhan et al., 2023). Wereldwijd wordt ongeveer 0,5% van mensen beïnvloed door RA (Deseatnicova et al., 2026). RA ontstaat door een combinatie van genetische en omgevingsfactoren waarbij roken een bekende risicofactor is. Een recente studie heeft een toename gevonden van RA-diagnoses over een periode van 32 jaar, van 11,66 naar 13,48 per 100,000 mensen (Zhang et al., 2025). 
Langdurige onbehandelde RA kan lijden tot gewrichtsmisvormingen, functieverlies, en erosie van kraakbeen en bot (Wang et al., 2019). Daarom is een vroegtijdige diagnose van groot belang. Hoewel er momenteel geen genezend medicijn bestaat, kan RA door medicatie en patiënten educatie worden geremd (Majithia & Geraci, 2007). Voor de ontwikkeling van nieuwe medicijnen kan transcriptomics een belangrijke rol spelen, omdat hiermee zichtbaar wordt welke genen en pathways differentieel tot expressie komen bij patiënten met RA in vergelijking met gezonde individuen. Deze inzichten kunnen bijdragen aan het begrijpen van het ontstaan en de progressie van de ziekte.

`Figuur 1; Weergave van Reumatoïde Artitis in een hand.`
<img width="632" height="632" alt="RA plaatje" src="https://github.com/user-attachments/assets/ee521a74-b11b-472b-844a-8541c6312540" />

# 2. Methode
Synoviumbiopten van vier patiënten met reumatoïde artritis (RA) en vier controles werden verzameld (fig. 2). Uit de biopten werden DNA geïsoleerd en RNA sequencing uitgevoerd. Het humane referentiegenoom werd geïndexeerd met Rsubread versie 2.14.2 en de reads daarop gemapt (Shi, 2022). Dit volgens standaardinstellingen van Rsubread. Resulterend zijn BAM bestanden. Met het GTF bestand GCF_000001405.40 werden reads per gen gekwantificeerd. Met DESeq2 versie 1.40.2 werd een count matrix geconstrueerd en differentiële genexpressie bepaald (Package “DESeq2,” 2025). Significante genen voldeden aan padj < 0,05. Voor visualisatie en functionele interpretatie zijn drie analyses uitgevoerd: een Volcano plot om opvallende genen te selecteren op basis van log2 fold change en bijgestelde p waarde, een KEGG padverrijkingsanalyse, gevisualiseerd met Pathview versie 1.40.0, om betrokken moleculaire routes te identificeren, en een Gene Ontology (GO) enrichmentanalyse (Bioconductor - EnhancedVolcano, n.d.; Gene Ontology Enrichment Analysis, n.d.; Title Client-Side REST Access to the Kyoto Encyclopedia of Genes and Genomes (KEGG), 2025; Maintainer & Luo, 2025). Bij GO enrichment lengtebias gecorrigeerd met goseq versie 1.52.0 en gebruikten org.Hs.eg.db versie 3.17.0 voor annotatie (hg19, geneSymbol) (Bioconductor - Goseq, n.d.; Bioconductor - Org.Hs.Eg.Db, n.d.). Overrepresentatietests werden gecorrigeerd met de Benjamini–Hochberg methode. Alle gebruikte R pakketten en versies zijn gedocumenteerd in het bijgevoegde R script.

`Figuur 2; Flowchart gemaakt met Lucidchart (Diagram Software | Lucidchart, n.d.). Synoviumbiopt is uitgevoerd op vier patiënten met RA en vier gezonde patiënten. Hieruit is DNA geïsoleerd en RNA sequencing uitgevoerd om RNA-seq-data te verkrijgen. Hiernaast is het humane referentie genoom verkregen via de NCBI databank, waarna deze is geïndexeerd (National Center for Biotechnology Information, n.d.). Samples zijn gemapt tegen het geïndexeerde genoom. Reads per gen kwantificeert met BAM-files van alle patiënten en het humane GTF-file. Count matrix is gemaakt en vervolgens statistische analyses uitgevoerd (KEGG pathway, Volcano plot en GO analyse).`
<img width="2636" height="632" alt="Flowchart transcriptomics casus RA" src="https://github.com/user-attachments/assets/d8382976-e858-4706-973e-79095677d853" />


# 3. Resultaten
De GO-analyse liet zien dat de tien meest significante gereguleerde genen betrokken zijn bij: chronische immuun activatie, versterkte signaalroutes, metabolisme, eiwit binding onderandere receptoren, oxidatieve stress, verhoogde cytokineproductie, inflammasomen en antigeen presentatie, zie figuur 5 en tabel Resultaten/GO_analyse.xlsx. Dit zijn allemaal bekende symptomen bij RA. 

`Figuur 3; Volcano plot van differentiële genexpressie gemaakt met behulp van het EnhancedVolcano package in R-studio. Dit op basis van 29407 variabelen. Weergegeven op de x-as is de Log2 fold change en op de y-as -log10 P. Hierbij zijn de drempels en geselecteerde genlabels zichtbaar. De grijs gekleurde genen hebben geen statisch significante differentiële genexpressie. De rood gekleurde genen hebben een hoge statistische significantie en zijn sterk verhoogd. Alle groen gekleurde genen zijn niet statistisch relevant volgens de gestelde eisen.`

<img width="632" height="632" alt="Correcte Volcanoplot2" src="https://github.com/user-attachments/assets/8b3924f8-55a8-4c68-8f7b-fe303e977dbb" />

`Figuur 4; KEGG pathway voor Reumatoïde Artitis (RA) gerendeerd met Pathview package in R-studio. Zichtbaar zijn alle betrokken genen bij RA. Bij een verhoogde differentiële expressie, zie IL6, ILS of MMP1/3, zijn de genen rood gekleurd. Bij een verlaagde differentiële expressie, zie VEGF, API en IL17, zijn de genen groen gekleurd. Bij geen verschil grijs.` 

<img width="1492" height="632" alt="Correcte pathview" src="https://github.com/user-attachments/assets/3e24040c-4504-4d3d-b974-85c7d4e2fb47" />

`Figuur 5; Puntdiagram van de uitgevoerde GO-enrichment resultaten. Zichtbaar op de x-as is het percentage Hits van de gedetecteerde top 10 gen ID’s per GO-term. Aangegeven op de y-as staan de GO-termen, hierbij is de grootte van de punten in samenhang met het aantal genen. De kleur van ieder punt is de p-waarde, hoe donkerder hoe significanter. Hoe hoger een GO-term hoe significanter deze tot expressie komt.` 

<img width="738" height="341" alt="GO analyse plot" src="https://github.com/user-attachments/assets/8e66ff42-615c-43fa-9028-b63aea5c0502" />


# 4. Conclusie

# 5. Beheer
 
