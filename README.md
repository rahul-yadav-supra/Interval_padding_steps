#### This repo shows the commands for creating a padded intervals file.


### Installing of the mysql client
`sudo apt install mysql-client-core-5.7`

### Getting chromosome size and info from ucsc for hg19
`mysql --user=genome --host=genome-mysql.cse.ucsc.edu -A -e "select chrom, size from hg19.chromInfo"  > hg19.genome`

### Creating a sorted file from the raw genome size file
`sed 's/chr//g' hg19.genome | sed '1s/om/chrom/' | sort -k1,1V > hg19_sorted.genome`

### Bedtools Padded Intervals file creation
`bedtools slop -i ~/Desktop/TOIL_TEST_DATA/Twist_Exome_Target_hg19.bed -b 20 -g hg19_sorted.genome > padded_interval_file.bed`
