---
title: PowerShell - foreach-object and break 
image: image
description: There is a common misconception of the use and break and foreach-object.
createddate: 01/06/2019
updateddate: 17/06/2020
tag: PowerShell
author: Charles Boudry
---

# PowerShell - foreach-object and break

I once reviewed a PowerShell code similar to this one :
```powershell
$is = 0..3
foreach($i in $is)
{
	$js = 0..3
	$js | %{
		$j = $_
		write-output "$i $j"
		if ($j -eq 2){break;}
	}
}
```
The usual expectation is the following : 
0 0
0 1
0 2
0 3
1 0
1 1
1 2
1 3
2 0
2 1
2 2
2 3
3 0
3 1
3 2
3 3

```powershell
for ($i=0; $i -lt 10 ; $i++){
	for ($j=0; $j -lt 10 ; $j++){
		write-output "$i $j"
		if ($j -eq 5){break;}
}}
```

```powershell
$is = 0..9
$js = 0..9
foreach($i in $is)
{
	foreach($j in $js)
	{
		write-output "$i $j"
		if ($j -eq 5){break;}
	}
}
```





```powershell
$is = 0..9
$js = 0..9
$is | foreach-object{
    $i = $_
	$js | foreach-object{
		$j = $_
		write-output "$i $j"
		if ($j -eq 5){break;}
	}
}
```
