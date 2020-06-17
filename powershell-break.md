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
for ($i=0; $i -lt 10 ; $i++){
	for ($j=0; $j -lt 10 ; $j++){
		write-output "$i $j"
		if ($j -eq 5){
			break;}
}}
```

```powershell
$is = 0..9
$js = 0..9
foreach($i in $is)
{
	$js | foreach-object{
		$j = $_
		write-output "$i $j"
		if ($j -eq 5){break;}
	}
}
```