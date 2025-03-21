# TFM_LeireAlkorta_VIU_Abril2025
Microbiome data analysis workflow combining two different datasets of UC patient amplicon data 

El código utilizado para el procesado y análisis de datos del Trabajo de Fin de Master 
"Análisis de la composición de la microbiota intestinal de pacientes con Colitis Ulcerosa" 
se encuentra en la carpeta "Code". 

El código utilizado en la parte de Pre-procesamiento se encuenta en el archivo data_preprocessing.Rmd
El código utilizado para la modificación de las tablas de metadatos para adecuarlos al análisis posterior se encuentra en el archivo metadata_preparation.Rmd
El código utilizado para el análisis de los datos se encuentra en el archivo data_analysis_corr.Rmd para el análisis de los datos combinados, y data_analysis_bp1.Rmd y data_analysis_bp2.Rmd para el análisis de los bioprojects individuales. 

Previamente a importar los datos a Rstudio, se siguió este proceso en Linux/AWS: 

Data download/import from SRA 
- Sratools - fastq-dump
xargs -n1 fastq-dump --gzip –split-3 < SRR_Acc_List.txt

Initial quality control 
- Fastqc (0.12.1)
fastqc *.fastq.gz --o ../../Processed/1_Quality_control_1/amp...
 -Multiqc (1.25.2)
multiqc .

Trimming
- TrimGalore! (0.6.10)
trim_galore *.fastq.gz -o ../../Processed/2_Trimming/amp_...

Second quality control
- Fastqc
fastqc *.fq.gz --o ../../3_Quality_control_2/amp...
- Multiqc (1.25.2)
multiqc .
