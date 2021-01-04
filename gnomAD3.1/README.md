# Population common alleles based on gnomAD 3.1

Several population go
| population               | abreviation | genomes | # `alt` > `ref` |
|-----------               |-------------|---------| --                 |
| African/African American | adj_afr     | 20,744  | 2,334,582          |
| Amish                    | adj_ami     | 456     | 2,435,528          |
| Latino/Admixed American  | adj_amr     |  7,647  | 2,343063          |
| Ashkenazi Jewish         | adj_asj     | 1,736   | 2,375,907          |
| East Asian               | adj_eas     | 2,604   | 2,579,504          |
| Finnish                  | adj_fin     | 5,316   | 2,364,824          |
| Middle Eastern           | adj_mid     | 158     | 2,346,917          |
| Non-Finnish European     | adj_nfe     | 34,029  | 2,369,937          |
| South Asian              | adj_sas     | 2,419   | 2,367,008          |
| Other                    |adj_oth      | 1,047   |  -          |
| **Total**                | adj         | 76,156  | 2,274,088          |

weblink: https://gnomad.broadinstitute.org/faq


\# `alt` > `ref`: count of alleles that the alternative allele have a higher allele frequency (**AF**) than alleles in the reference genome.


files are in csv format (with `\t` as separator), which looks like:

|   chr |   pos | ref   | alt   |   alt_AF |   ref_AF |
|------:|------:|:------|:------|---------:|---------:|
|     1 | 10146 | AC    | A     |   0.6328 |   0.3672 |
|     1 | 15274 | A     | G     |   0.6311 |   0.0635 |
|     1 | 28563 | A     | G     |   0.6842 |   0.3158 |
|     1 | 49298 | T     | C     |   0.5852 |   0.4148 |
|     1 | 52238 | T     | G     |   0.9013 |   0.0987 |
