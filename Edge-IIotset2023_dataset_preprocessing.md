# Edge-IIoTset2023 dataset pre-processing

To aid in reproducibility efforts by future researchers, the dataset pre-processing steps are described in this section.

The Edge-IIoTset2023 dataset can be downloaded from https://ieee-dataport.org/documents/edge-iiotset-new-comprehensive-realistic-cyber-security-dataset-iot-and-iiot-applications

The Edge-IIoTset2023 dataset has already undergone some pre-processing.  The network packet capture (pcap) files have already been converted to CSV format.  In com-pressed form, the dataset consumes ~1.5GB of disk space, and after uncompressing, ex-pands to ~12GB of disk space.
```
$ du -sh 'Edge-IIoTset dataset.zip'
1.5G

$ unzip 'Edge-IIoTset dataset.zip'
$ du -sh .
12G     total
```

There are 51 files in the Edge-IIoTset2023 dataset, with the filenames listed below:
```
$ find /datasets/Edge-IIoTset2023 -type f  | wc -l
51

$ find /datasets/Edge-IIoTset2023 -type f
/datasets/Edge-IIoTset2023/Edge-IIoTset dataset.zip
/datasets/Edge-IIoTset2023/Attack traffic/Backdoor_attack.csv
/datasets/Edge-IIoTset2023/Attack traffic/Backdoor_attack.pcap
/datasets/Edge-IIoTset2023/Attack traffic/DDoS HTTP Flood Attacks.pcap
/datasets/Edge-IIoTset2023/Attack traffic/DDoS ICMP Flood Attacks.pcap
/datasets/Edge-IIoTset2023/Attack traffic/DDoS TCP SYN Flood Attacks.pcap
/datasets/Edge-IIoTset2023/Attack traffic/DDoS UDP Flood Attacks.pcap
/datasets/Edge-IIoTset2023/Attack traffic/DDoS_HTTP_Flood_attack.csv
/datasets/Edge-IIoTset2023/Attack traffic/DDoS_ICMP_Flood_attack.csv
/datasets/Edge-IIoTset2023/Attack traffic/DDoS_TCP_SYN_Flood_attack.csv
/datasets/Edge-IIoTset2023/Attack traffic/DDoS_UDP_Flood_attack.csv
/datasets/Edge-IIoTset2023/Attack traffic/MITM (ARP spoofing + DNS) Attack.pcap
/datasets/Edge-IIoTset2023/Attack traffic/MITM_attack.csv
/datasets/Edge-IIoTset2023/Attack traffic/OS Fingerprinting attack.pcap
/datasets/Edge-IIoTset2023/Attack traffic/OS_Fingerprinting_attack.csv
/datasets/Edge-IIoTset2023/Attack traffic/Password attacks.pcap
/datasets/Edge-IIoTset2023/Attack traffic/Password_attack.csv
/datasets/Edge-IIoTset2023/Attack traffic/Port Scanning attack.pcap
/datasets/Edge-IIoTset2023/Attack traffic/Port_Scanning_attack.csv
/datasets/Edge-IIoTset2023/Attack traffic/Ransomware attack.pcap
/datasets/Edge-IIoTset2023/Attack traffic/Ransomware_attack.csv
/datasets/Edge-IIoTset2023/Attack traffic/SQL injection attack.pcap
/datasets/Edge-IIoTset2023/Attack traffic/SQL_injection_attack.csv
/datasets/Edge-IIoTset2023/Attack traffic/Uploading attack.pcap
/datasets/Edge-IIoTset2023/Attack traffic/Uploading_attack.csv
/datasets/Edge-IIoTset2023/Attack traffic/Vulnerability scanner attack.pcap
/datasets/Edge-IIoTset2023/Attack traffic/Vulnerability_scanner_attack.csv
/datasets/Edge-IIoTset2023/Attack traffic/XSS attacks.pcap
/datasets/Edge-IIoTset2023/Attack traffic/XSS_attack.csv
/datasets/Edge-IIoTset2023/Normal traffic/Distance/Distance.csv
/datasets/Edge-IIoTset2023/Normal traffic/Distance/Distance.pcap
/datasets/Edge-IIoTset2023/Normal traffic/Flame_Sensor/Flame_Sensor.csv
/datasets/Edge-IIoTset2023/Normal traffic/Flame_Sensor/Flame_Sensor.pcap
/datasets/Edge-IIoTset2023/Normal traffic/Heart_Rate/Heart_Rate.csv
/datasets/Edge-IIoTset2023/Normal traffic/Heart_Rate/Heart_Rate.pcap
/datasets/Edge-IIoTset2023/Normal traffic/IR_Receiver/IR_Receiver.csv
/datasets/Edge-IIoTset2023/Normal traffic/IR_Receiver/IR_Receiver.pcap
/datasets/Edge-IIoTset2023/Normal traffic/Modbus/Modbus.csv
/datasets/Edge-IIoTset2023/Normal traffic/Modbus/Modbus.pcap
/datasets/Edge-IIoTset2023/Normal traffic/phValue/phValue.csv
/datasets/Edge-IIoTset2023/Normal traffic/phValue/phValue.pcap
/datasets/Edge-IIoTset2023/Normal traffic/Soil_Moisture/Soil_Moisture.csv
/datasets/Edge-IIoTset2023/Normal traffic/Soil_Moisture/Soil_Moisture.pcap
/datasets/Edge-IIoTset2023/Normal traffic/Sound_Sensor/Sound_Sensor.csv
/datasets/Edge-IIoTset2023/Normal traffic/Sound_Sensor/Sound_Sensor.pcap
/datasets/Edge-IIoTset2023/Normal traffic/Temperature_and_Humidity/Temperature_and_Humidity.csv
/datasets/Edge-IIoTset2023/Normal traffic/Temperature_and_Humidity/Temperature_and_Humidity.pcap
/datasets/Edge-IIoTset2023/Normal traffic/Water_Level/Water_Level.csv
/datasets/Edge-IIoTset2023/Normal traffic/Water_Level/Water_Level.pcap
/datasets/Edge-IIoTset2023/Selected dataset for ML and DL/DNN-EdgeIIoT-dataset.csv
/datasets/Edge-IIoTset2023/Selected dataset for ML and DL/ML-EdgeIIoT-dataset.csv
```

The dataset has already undergone some pre-processing, this is the file we are interested in, which has already been encoded into CSV format.  
```
$ cd /datasets/Edge-IIoTset2023/Selected_dataset_for_ML_and_DL
$ cp DNN-EdgeIIoT-dataset.csv ..
```

Calculate the total number of lines (rows) in the CSV data file.
```
$ wc -l DNN-EdgeIIoT-dataset.csv
2219202 DNN-EdgeIIoT-dataset.csv
```
Use the following syntax to count the number of commas in the header row, which indicates the number of columns (features) in the dataset.  
Please note that since the last column in the CSV file is not followed by a comma, the number of features is one greater than the calculation below:
```
$ cat DNN-EdgeIIoT-dataset.csv | head -n 1 | grep -o , | wc -w
62
```

Calculate how imbalanced the dataset is by searching for the label “Normal” in the CSV file.
```
$ grep    ",Normal" DNN-EdgeIIoT-dataset.csv | wc -l
1615643

$ grep -v ",Normal" DNN-EdgeIIoT-dataset.csv | wc -l
603559
```

This dataset has 603559/(603559+1615643) * 100 = 27.2% anomaly data, and (100-27.2)=72.8% normal data.  However, a large portion of the attack data is Distributed Denial of Service (DDoS), which is very “noisy”, thus polluting the dataset with low-quality data.  Since DDoS attacks can be considered as a threshold-based metric, they are best addressed via perimeter firewalls rather than in a ML model, so we will drop the DDoS entries from the dataset.
```
$ cat DNN-EdgeIIoT-dataset.csv | grep -v DDoS > DNN-EdgeIIoT-dataset2.csv
```

Now check the class balance again after removing the DDoS traffic.
```
$ grep    ",Normal" DNN-EdgeIIoT-dataset2.csv | wc -l
1615643

$ grep -v ",Normal" DNN-EdgeIIoT-dataset2.csv | wc -l
265582
```

After removing the noisy DDoS traffic, this dataset has 265582/(265582+1615643) * 100 = 14.1% anomaly data, and (100-14.1)=85.9% normal data.  

At this point, the Edge-IIoTset2023 dataset has been sufficiently cleaned, and is ready to be imported into a machine learning environment for further analysis and model training.  
