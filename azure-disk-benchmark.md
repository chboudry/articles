---
metadata-title: Azure Disk - Benchmark
metadata-image: automation
metadata-description: Describes the different methods for starting a runbook in Azure Automation from another runbook and sharing information between them.
metadata-createddate: 01/17/2019
metadata-updateddate: 01/17/2019
metadata-tag: Azure
metadata-author: Charles Boudry
---

# Azure Disk - Benchmark

https://docs.microsoft.com/en-us/azure/virtual-machines/windows/disks-benchmarks
https://docs.microsoft.com/en-us/azure/virtual-machines/linux/sizes-storage

https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes-general 
Standard_D2s_v3
Size	vCPU	Memory: GiB	Temp storage (SSD) GiB	Max data disks	Max cached and temp storage throughput: IOPS / MBps (cache size in GiB)	Max uncached disk throughput: IOPS / MBps	Max NICs / Expected network bandwidth (Mbps)
Standard_D2s_v3	2	8	16	4	4000 / 32 (50)	3200 / 48	2 / 1000

Recommandations for SQL Server : https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance

NEXT STEP : MATCH IOMETER TO PERFMON COUNTERS ON WINDOWS
