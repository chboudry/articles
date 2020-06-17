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

## 
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
| Customer's expectation  | The actual result |
| ------------- | ------------- |
| 0 0<br>0 1<br>0 2<br>0 3<br>1 0<br>1 1<br>1 2<br>1 3<br>2 0<br>2 1<br>2 2<br>2 3<br>3 0<br>3 1<br>3 2<br>3 3 | 0 0<br>0 1<br>0 2  |

## Explanation


