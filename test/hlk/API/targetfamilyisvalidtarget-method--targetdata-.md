---
title: TargetFamily.IsValidTarget Method (TargetData)
description: TargetFamily.IsValidTarget Method (TargetData)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: be8be52c-34b6-432c-bf76-bbcd5d4f2e46
author: sapaetsc
ms.author: sapaetsc
ms.date: 10/15/17
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# TargetFamily.IsValidTarget Method (TargetData)


This method determines whether the specified TargetData can be a member of this TargetFamily.

**Namespace:** Microsoft.Windows.Kits.Hardware.ObjectModel

**Assembly:** Microsoft.Windows.Kits.Hardware.ObjectModel (in Microsoft.Windows.Kits.Hardware.ObjectModel)

## <span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Syntax


**Visual Basic**

`Public Function IsValidTarget ( _`

          `target As TargetData _`

`) As Boolean`

**C#**

`public bool IsValidTarget (`

          `TargetData target`

`)`

## <span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>Parameters


*target*

     Target data to examine.

## <span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>Return Value


Returns **bool**.

## <span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks


The following conditions determine validity.

1.  The Machine of the target is in the same machine pool as the ProductInstance.

2.  The Machine of the target has the same OS Platform as the ProductInstance (parent) object.

3.  All targets having common manufacturer/VID/Ven.

4.  All targets having common driver hash (of all drivers associated with this device, including any upper and lower filters).

5.  All targets having a common INF hash.

6.  All targets having the same bus/enumerator type.

7.  All targets having the same class/subclass.

8.  If DX capable, same DX major version.

9.  All targets are on unique machines not already part of the TargetFamily. Note that different targets under a product instance are supported on one machine.

10. All targets must be in the running state.

11. Each machine associated with the Target family is running the same version of the OSPlatform as the product instance.

If any of the checks fail, the method returns false.

This specifically allows different Device ID, PID (Product Id) or “Dev” and different sub vendor or implementer Ids.

If the comparison fails, this method populates the event log with additional data.

## <span id="Thread_Safety"></span><span id="thread_safety"></span><span id="THREAD_SAFETY"></span>Thread Safety


Any public static (**Shared** in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

 

 






