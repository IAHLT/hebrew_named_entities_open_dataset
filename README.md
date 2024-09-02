# Named Entities Dataset for Hebrew

האיגוד הישראלי לטכנולוגיות שפת אנוש
الرابطة الإسرائيلية لتكنولوجيا اللغة البشرية

The Israeli Association of Human Language Technologies
https://www.iahlt.org

Our named entities dataset for Hebrew.

## Introduction

The IAHLT named entities corpus consists of  articles from the Davar
news paper (47%), the Israel Hayom news paper (24%),
Knesset protocols (2%) and Wikipedia entries (27%).

The raw text was manually annotated following [these guidelines](https://github.com/IAHLT/hebrew_named_entities_open_dataset/blob/main/he-guidelines.pdf) to identify entity spans and automatically
corrected for whitespace- and punctuation-alignment. A portion of the spans
were then scanned for potential errors and manually reviewed for quality
assurance. Spans are allowed to nest. 

## Dataset

This release consists of 27,140 paragraphs from 2,970 articles. They have been
annotated on the morpheme level.

The current release includes the following files:

### Datasets (.jsonl):

- `all_hebrew_samples_with_duplicates.jsonl`  
  Contains all Hebrew samples, including duplicates.

- `unique_hebrew_samples_no_duplicates.jsonl`  
  Contains the best Hebrew samples, with duplicates removed.

- `hebrew_samples_first_annotation.jsonl`  
  Includes one annotation from each of the multiply-annotated samples.

- `hebrew_samples_second_annotation.jsonl`  
  Contains a second annotation from each of the multiply-annotated samples.


Every line in those files is a single JSON dictionary. Each dictionary has the following keys:
- text     -- the annotated text
- label    -- an array of triples `[<start>, <end>, <label>]`; `<start>` is the
  first Unicode graph of the label, `<end>` is the first Unicode graph *after*
  the label, and `<label>` is the entity type
- metadata -- a dictionary of metadata identifying the origin of the text and
  its review level

Entity spans were manually made at the grapheme-level, then automatically
whitespace- and punctuation-aligned using language-aware rules.

## Metadata fields

  * Here are some fields for technical considerations:

    * `url`        - the link for the source entry/article
    * `source`     - the source of the text
    * `doc_id`     - a unique identifier for the source document
    * `parnumber`  - the paragraph sequence number within the source document
    * `sentnumber` - the sentence sequence number within the source paragraph

  * fields indicating elevated confidence level:

    * (high confidence) `manually_qa-ed` - indicates for each annotation whether
      it has been manually validated following errors found by the QA script

## Entity Types

Here are the entity types we annotated, along with the number of instances in the entire corpus:

| Type | # Instances |
| :---   | ---: |
| ANG | 549 |
| DUC | 2,014 |
| EVE | 4,852 |
| FAC | 5,230 |
| GPE | 36,899 |
| INFORMAL | 180 |
| LOC | 6,276 |
| MISC | 8,578 |
| ORG | 40,892 |
| PER | 44,498 |
| TIMEX | 15,092 |
| TTL | 16,181 |
| WOA | 4,255 |

The distribution by source:
  
              Wikipedia   Knesset   Israel_Hayom   Davar
    docs      66          274       775            1855
    pars      2323        409       7685           15185
    ------    ----------  --------  -------------  ------
    PER       9570        371       11110          23447
    ORG       5150        617       7118           28007
    GPE       5681        362       8604           22252
    TTL       1740        173       2314           11954
    TIMEX     4600        109       1709           8674
    MISC      2996        84        2046           3452
    LOC       1503        62        1379           3332
    FAC       1645        38        824            2723
    EVE       1071        38        651            3092
    WOA       2233        6         1132           884
    DUC       366         10        875            763
    ANG       210         7         80             252
    INFORMAL  4           1         175            0
    (total)   36769       1878      38017          108832
 

The 10 most frequent entities of each type:

    entity    mafat-2024-08-12-heb.jsonl
    ------    --------------------------
    PER       44498(11904 unique)
            נתניהו(1085)
            טראמפ(865)
            איינשטיין(550)
            בנט(368)
            ביבי(303)
            בנימין נתניהו(270)
            ליברמן(269)
            עגנון(204)
            פולארד(197)
            כחלון(185)
   
    ORG       40892(7312 unique)
            צה"ל(1381)
            הכנסת(1049)
            ההסתדרות(851)
            משרד הבריאות(832)
            האוצר(733)
            כנסת(683)
            חמאס(550)
            בית המשפט העליון(489)
            משרד האוצר(420)
            בזק(291)
   
    GPE       36899(2493 unique)
            ישראל(8212)
            ירושלים(1900)
            ארה"ב(1319)
            תל אביב(930)
            סוריה(796)
            חיפה(795)
            גרמניה(724)
            רוסיה(697)
            עזה(688)
            איראן(578)
   
    TTL       16181(2942 unique)
            ראש הממשלה(864)
            ח"כ(807)
            ד"ר(545)
            הנשיא(474)
            יו"ר(450)
            פרופ'(450)
            שר(423)
            עו"ד(399)
            השר(284)
            השופט(272)
   
    TIMEX     15092(2343 unique)
            שבת(336)
            חמישי(313)
            ראשון(310)
            שני(282)
            רביעי(269)
            שלישי(265)
            2017(259)
            2018(232)
            2015(219)
            2019(216)
   
    MISC      8578(1934 unique)
            קורונה(1197)
            הקורונה(233)
            אינסולין(218)
            סוכרת(213)
            פניצילין(208)
            אומיקרון(179)
            אלוהים(132)
            חוק ההסדרים(125)
            סרטן(120)
            גלוקוז(104)
   
    LOC       6276(888 unique)
            אירופה(656)
            ארץ ישראל(280)
            רצועת עזה(233)
            אפריקה(192)
            יהודה ושומרון(186)
            נגב(186)
            רמת הגולן(124)
            עוטף עזה(100)
            ים המלח(96)
            שומרון(92)
   
    FAC       5230(1928 unique)
            מצדה(224)
            נמל אשדוד(80)
            כנסיית הקבר(77)
            נתב"ג(58)
            מערת ה מכפלה(57)
            הר הבית(56)
            לוויתן(50)
            העיר הלבנה(50)
            תמר(48)
            בית הלבן(47)
   
    EVE       4852(1407 unique)
            משבר הקורונה(194)
            השואה(193)
            שואה(134)
            אליפות אירופה(79)
            מלחמת העולם השנייה(74)
            אירוויזיון(69)
            הקורונה(63)
            יום העצמאות(62)
            צוק איתן(62)
            מלחמת ששת הימים(50)
   
    WOA       4255(2072 unique)
            תורה(94)
            תנ"ך(40)
            דבר(40)
            האח הגדול(31)
            קוראן(29)
            שבלול(27)
            דברים כ:י-יח(22)
            ארץ נהדרת(21)
            ירושלים של זהב(19)
            במדבר לג:נב(19)
   
    DUC       2014(644 unique)
            פייסבוק(173)
            טוויטר(133)
            ישראל היום(110)
            במבה(104)
            אינסטגרם(81)
            זום(38)
            גוגל(27)
            הפייסבוק(22)
            נטפליקס(22)
            וואטסאפ(21)
   
    ANG       549(57 unique)
            עברית(155)
            ערבית(83)
            אנגלית(56)
            יידיש(42)
            רוסית(34)
            העברית(17)
            ספרדית(17)
            יוונית(16)
            לטינית(12)
            גרמנית(11)
   
    INFORMAL  180(133 unique)
            מחורבנט(7)
            אייזנפלוץ(5)
            יהיר לפיד(5)
            משרד הורסי הבריאות(4)
            שאשא קאקא(4)
            חרבנט(4)
            דגלובסקי(4)
            חוסיין אובמה(3)
            שפטל דמניוק(3)
            דוברמן(3)
   

## Inter-annotator agreement

A subsample of our dataset (20% heb) was doubly-annotated in order to
evaluate our guidelines and annotation process.  We compute character-wise
Cohen's kappa for each entity type:

    (total)   0.64643
    ANG       0.605859
    DUC       0.597468
    EVE       0.604526
    FAC       0.565302
    GPE       0.685116
    INFORMAL  0.619491
    LOC       0.557783
    MISC      0.483612
    ORG       0.725078
    PER       0.67413
    TIMEX     0.54547
    TTL       0.687955
    WOA       0.541171
 

## Acknowledgments

We would like to thank all the people who contributed to this corpus:

Alice Kamishan </br>
Amir Ejmail</br>
Amjad Aliat</br>
Ammar Ammash</br>
Emmanuelle Kowner</br>
Georgie Nustas</br>
Israel Landau</br>
Maayan Orner</br>
Majd Shalash</br>
Mutaz Ayesh</br>
Nathan Dahan</br>
Nick Howell</br>
Noam Ordan</br>
Omer Strass</br>
Razan Assi</br>
Sawsan Thabit</br>
Shahar Adar</br>
Shira Wigderson</br>
Yaara Ben Aharon</br>
Yael Minerbi</br>
Yifat Ben Moshe</br>
Yousef Tannous

