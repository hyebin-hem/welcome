# QIIME2 API

### Update note

- **version 0.06 updated at Jul 28th 2021**
- API tested on QIIME2 ver.2021.02 on Ubuntu 20.04 LTS with anaconda3
- Added feature filtering step (for myLAB report)
- included feature filtering step in pipeline_full
- upload `asv_list.txt` file for feature filtering step

## 1. Spec

- QIIME2 ver : 2021.02
- Reference DB : SILVA_ver0.02
- Classifier region : V3-V4 of 16S rRNA gene
- Denoising : DADA2
- Paired-End sequencing pipeline (250bp x 2)
- (option) Feature filtering (myLAB reference 기준)

## 2. File list

- `qiimeAPI_500cycle.py` : Module [required]
- `qiimeAPI_Run.html` :
- `qiimeAPI_Run.ipynb` : API run jupyter notebook [required]
- `asv_list.txt` : Feature filtering metadata, if 'myLAB=True', it required [option]

## 3. Run

1. activate QIIME2
2. open `qiimeAPI_Run.ipynb`
3. Set the variable and import module
4. Run full pipeline or each funtion

## 4. Variable

코드 실행 시, workdir 하위에 [seqfolder, qiimeAPI_500cycle.py, silva classifier, asv_list]외의 다른 파일 및 폴더가 없는 것을 권장함

- `moduledir`

    qiimeAPI_500cycle.py 파일의 폴더 경로

    moduledir와 workdir는 동일해도 무방

- `workdir`

    Run할 fastq데이터가 포함된 seqfolder (ex. HEM######), classifier, asv.txt 가 포함된 
    작업할 폴더 경로

- `seqfolder`

    fastq 폴더명 (폴더명은 'HEM+6자리 or 8자리 숫자' 형태만 사용 가능)

- `qiime_ver`

    사용중인 qiime2 버전 (2020.6 이후 버전 권장)

    QIIME2 ver.2021.4 사용 시 '21.4'로 표기

- `myLAB`

    myLAB 결과지 제작을 위한 추가 과정 진행 여부

    myLAB sample 포함시 True, 미포함시 False 표기

## 5. Output

 `qiime_ver = '21.2', myLAB= True` Full pipeline (from fastq to csv) output

폴더는 Bold, 생성된 output은 파란색으로 표기

<details>
<summary>workdir</summary>
    <details>
    <summary>seqfolder (ex.HEM######) </summary>
        sample1_R1_001.fastq.qz
        sample1_R2_001.fastq.qz
        ......
        metadata.txt
        manifest.txt
        rep-seqs.qza
        table.qza
        .......
    </details>
    <details>
    <summary>csvfiles (final output file : 11) </summary>
        level1~7.csv
        shannon.csv
        sequences.csv
        feature-table.csv
        taxonomy-silva138_v0.02.csv
    </details>
    <details>
    <summary>myLAB</summary>
        filtered-rep-seqs.qza
        filtered-table.qza
        taxa-bar-plot-silva138_v0.02.qza
    ........
    <details>
    <summary>csvfiles</summary>
        level-1~7.csv (feature filtered)
        shannon.csv (copied)
        taxonomy-silva138_v0.02.csv (feature filtered)
    </details>
    - silva138v0.02_classifier21.2.qza
    - asv_list.txt
</details>