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

## Context
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

We can observe that the `break` statement is not only breaking the `foreach-object` (written %) but the parent `foreach` as well.

## Explanation

Looking a bit on the Internet I found multiple weird hypothesis about the pipeline usage.

Reality is much simpler than that : foreach-object is a PowerShell Cmdlet and not a statement : you just can't use `break` with `foreach-object`.

This can be confirmed with the following documentation :

https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_break


>**Short description**
>
>Describes a statement you can use to immediately exit foreach, for, while, do, switch, or trap statements.
>
>When `break` is used outside of a construct that directly supports it (`loops`, `switch`, `trap`), PowerShell looks up the call stack >for an enclosing construct. If it can't find an enclosing construct, the current runspace is quietly terminated.
>
>This means that functions and scripts that inadvertently use a break outside of an enclosing construct that supports it can >inadvertently terminate their callers.

In our example using `break` inside a pipeline using a ForEach-Object script block, not only exits the pipeline, it also terminates the parent. In worst case it can also potentially terminates the entire runspace (but that would have been easier to troubleshoot :wink:).
