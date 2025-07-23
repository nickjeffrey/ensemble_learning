# CICIoT2023 dataset pre-processing

To aid in reproducibility efforts by future researchers, the dataset pre-processing steps are described in this section.

The CICIoT2023 dataset can be downloaded from https://www.unb.ca/cic/datasets/iotdataset-2023.html

The dataset has already undergone some pre-processing.  The network packet capture (pcap) files have already been converted to CSV format.  In compressed form, the da-taset consumes ~2.7GB of disk space, and after uncompressing, increases in size to ~13GB.
```
$ du -sh CICIoT2023.zip
2.7G

$ unzip CICIoT2023.zip
$ du -ch part*.csv | tail -n 1
13G     total
```

There are 169 files in the dataset, with the filenames shown below:
```
$ find /datasets/CIC_IOT_Dataset2023/csv -type f -name "*.csv" | wc -l
169

$ find /datasets/CIC_IOT_Dataset2023/csv -type f -name "*.csv"
/datasets/CIC_IOT_Dataset2023/csv/part-00092-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00037-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00014-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00066-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00115-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00001-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00048-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00118-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00027-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00011-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00055-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00042-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00021-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00017-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00107-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00104-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00068-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00141-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00084-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00024-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00100-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00088-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00146-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00004-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00032-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00009-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00167-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00007-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00083-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00031-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00151-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00129-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00155-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00070-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00082-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00040-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00158-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00081-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00003-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00019-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00160-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00159-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00108-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00105-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00102-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00044-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00150-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00034-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00154-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00161-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00016-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00050-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00163-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00006-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00101-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00018-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00126-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00168-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00056-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00148-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00120-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00054-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00046-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00073-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00080-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00087-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00026-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00038-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00110-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00058-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00020-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00063-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00147-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00030-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00012-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00013-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00000-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00132-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00047-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00143-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00135-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00128-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00061-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00133-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00119-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00114-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00157-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00005-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00069-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00090-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00099-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00139-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00089-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00085-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00086-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00053-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00134-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00117-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00097-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00144-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00065-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00116-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00059-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00008-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00121-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00074-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00045-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00122-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00124-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00049-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00106-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00043-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00051-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00028-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00010-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00029-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00022-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00103-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00035-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00112-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00093-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00060-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00096-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00156-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00137-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00123-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00130-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00091-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00142-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00072-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00023-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00109-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00064-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00067-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00015-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00111-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00002-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00071-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00094-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00057-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00078-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00153-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00077-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00039-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00036-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00162-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00062-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00145-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00075-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00095-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00165-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00136-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00041-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00052-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00131-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00149-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00152-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00098-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00138-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00076-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00025-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00164-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00127-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00033-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00125-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00166-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00140-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00079-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
/datasets/CIC_IOT_Dataset2023/csv/part-00113-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv
```

Calculate the total number of lines in all the CSV data files
```
$ find /datasets/CIC_IOT_Dataset2023/csv -type f -name "*.csv" | xargs wc -l | tail -n 1
   46,686,748 total
```

Merge all the CSV files into a single file.
Each of the 169 CSV files contains a header row that looks similar to:
```
flow_duration, Header_Length, Protocol Type,Duration,Rate, Srate, Drate, fin_flag_number, syn_flag_number, rst_flag_number, psh_flag_number, ack_flag_number, ece_flag_number, cwr_flag_number, ack_count, syn_count, fin_count, urg_count, rst_count, HTTP, HTTPS, DNS, Telnet, SMTP, SSH, IRC, TCP, UDP, DHCP, ARP, ICMP, IPv, LLC, Tot sum, Min, Max, AVG, Std, Tot size, IAT, Number, Magnitue, Radius, Covariance, Variance, Weight, label
```

Get the header row into the new merged file:
```
$ head -n 1 part-00000-363d1ba3-8ab5-4f96-bc25-4d5862db7cb9-c000.csv > merged.csv
```

Use a loop to append all the CSV files (minus the header row) into a new merged file.  Please note that this will read and write 16GB worth of data, so be sure you have enough free space.
```
$ find /datasets/CIC_IOT_Dataset2023/csv -type f -name "part*.csv" | sort | while read filename ; do echo $filename ; cat $filename | grep -v ^flow_duration >> merged.csv ; done
```

The number of lines in the new merged file is ~46 million, which is 168 lines less than the line counts of all the individual CSV files, because each of the individual files had a head-er row.
```
$ wc -l merged.csv
46,686,580 merged.csv
```

Use the following syntax to count the number of commas in the header row, which indicates the number of columns (features) in the dataset.  Please note that since the last column in the CSV file is not followed by a comma, the number of features is one greater than the calculation below:
```
$ cat merged.csv      | head -n 1 | grep -o , | wc -w
46
```

The size of the merged CSV file is 13GB
```
$ du -sh  merged.csv
13G     merged.csv
```

Determine all the different attack types in the dataset
```
$ cat merged.csv | cut -d , -f 47 | sort | uniq
Backdoor_Malware
BenignTraffic
BrowserHijacking
CommandInjection
DDoS-ACK_Fragmentation
DDoS-HTTP_Flood
DDoS-ICMP_Flood
DDoS-ICMP_Fragmentation
DDoS-PSHACK_Flood
DDoS-RSTFINFlood
DDoS-SlowLoris
DDoS-SYN_Flood
DDoS-SynonymousIP_Flood
DDoS-TCP_Flood
DDoS-UDP_Flood
DDoS-UDP_Fragmentation
DictionaryBruteForce
DNS_Spoofing
DoS-HTTP_Flood
DoS-SYN_Flood
DoS-TCP_Flood
DoS-UDP_Flood
Mirai-greeth_flood
Mirai-greip_flood
Mirai-udpplain
MITM-ArpSpoofing
Recon-HostDiscovery
Recon-OSScan
Recon-PingSweep
Recon-PortScan
SqlInjection
Uploading_Attack
VulnerabilityScan
XSS
```


Calculate how imbalanced the dataset is by searching for the label “BenignTraffic” in the CSV file.
```
$ grep BenignTraffic merged.csv | wc -l
1098195

$ grep -v BenignTraffic merged.csv | wc -l
45588385
```

This dataset has 45,588,385 / (1,098,195 + 45,588,385) * 100 = 97.6% attack data, and 2.4% benign data.  That seems to be a very high ratio of attack data.  
Let’s take a look and see if there is any DDoS or flooding types of attacks that might be skewing the ratios.

Calculate how much of that data is DoS and DDoS and flood traffic:
```
$ cat merged.csv | grep -E ",DoS-|,DDoS-|_Flood|_flood" | wc -l
43,818,846
```


Remove the DoS and DDoS and flood traffic, as those are better detected with a thresh-old-based strategy.
```
$ cat merged.csv | grep -E -v ",DoS-|,DDoS-|_Flood|_flood" > merged_filtered.csv
$ wc -l merged_filtered.csv
2,867,734 merged_filtered.csv
```

After dropping the DDoS traffic, calculate how imbalanced the dataset is.  We can search for the label “BenignTraffic” in the CSV file.
```
$ grep    BenignTraffic merged_filtered.csv | wc -l
1,098,195

$ grep -v BenignTraffic merged_filtered.csv | wc -l
1,769,539
```

This dataset has 1,769,539 / (1,098,195 + 1,769,539) * 100 = 61.7% attack (anomaly) data, and 38.3% benign (normal) data.

At this point, the dataset has been sufficiently cleaned, and is ready to be imported into a machine learning environment for further analysis and model training.  
