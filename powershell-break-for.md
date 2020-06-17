---
title: PowerShell - Break with nested loops 
image: image
description: break has a very different comportment whether you are in a for each or in a for loop. Let's understand why.
createddate: 01/06/2019
updateddate: 17/06/2020
tag: PowerShell
author: Charles Boudry
---

# PowerShell - Break with nested loops

```powershell
Get-Command -Name Clear-Host
```
```text
CommandType Name Definition
Function Clear-Host $spaceType = [System.Managem...
```

```powershell
for ($i=1; $i -lt 10 ; $i++){
	for ($j=1; $j -lt 10 ; $j++){
		write-output "$i $j"
		if ($j -eq 5){
			break;}
}}
```

```powershell
$is = "1","2","3","4","5", "6", "7", "8", "9"
$js = "1","2","3","4","5", "6", "7", "8", "9"
foreach($i in $is)
{
	$js | foreach-object{
		$j = $_
		write-output "$i $j"
		if ($j -eq 5){break;}
	}
}
```
