!/usr/bin/bash -l
# 2022_hw2_template
#HW2 - explore CalFire data
# Write a shell script called `count_fires.sh` which does all of the following.
# Download a comma delimited datasets from https://data.cnra.ca.gov/  which are listing of fires in several decades larger than 5000+. search for "Recent Large Fire Perimiters" in the search box. Click on the dataset it should take you to [this page](https://data.cnra.ca.gov/dataset/recent-large-fire-perimeters-5000-acres1). Download the [CSV file](https://gis.data.cnra.ca.gov/datasets/CALFIRE-Forestry::recent-large-fire-perimeters-5000-acres.csv). (hint use `curl`).
git clone git@github.com:biodataprog/2022_hw2-lshad003.git

  # Print out the range of years that occur in this file (hint cut out the column you want, sort and get either the smallest or largest number)
cut -d, -f2 calfires_2021.csv | sort -n

  # Print out the number of fires in the database (hint use `wc`, remove the header or subtract out the rows )
cut -d, -f2 calfires_2021.csv | sort -n | wc -l

  # Print out the number of fires that occur each year (hint use `cut`, `sort` and `uniq -c`)
cut -d, -f2 calfires_2021.csv | sort -n | uniq -c | tail -n 5

  # Print out the name largest fire (hint use `sort`) - use the `GIS_ACRES` column
awk -F, '{print $13,$6}' calfires_2021.csv | sort -n

  # Print out the total acreage burned in each year.

        for YEAR in $(2017 2018 2019 2020 2021)
        do
           TOTAL=$(grep $YEAR Calfir_2021.csv| awk awk -F',' '{sum+=$13;} END{print sum;}'))
           echo "In Year $YEAR, Total was $TOTAL"

        done
