---
title: ServicePointManager.s_ServicePointTable alan
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type: apiref
api_name: System.Net.ServicePointManager.s_ServicePointTable
api_location: System.dll
api_type: Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f12a8ba4d2b84e5b5d73d26199adf687a95a2df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable alan

`ServicePointManager.s_ServicePointTable`olan bir <xref:System.Collections.Hashtable> etkin HTTP bağlantıları listesini içeren (<xref:System.Net.ServicePoint>s) içindeki <xref:System.AppDomain>.

## <a name="syntax"></a>Sözdizimi
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable` Alandır özel ve kodunuzda doğrudan kullanılmak üzere yüksetlmesi.
> 
> Microsoft hiçbir koşulda bir üretim uygulamasında bu alan kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Namespace:**<xref:System.Net>

**Derleme:** sisteminde (System.dll)

**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.
