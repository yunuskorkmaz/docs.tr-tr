---
title: ServicePointManager.s_ServicePointTable alan
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 5450a0cb3e5bd39a86365b16d372c7e573a43496
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351764"
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable alan

`ServicePointManager.s_ServicePointTable` olan bir <xref:System.Collections.Hashtable> etkin HTTP bağlantıları listesini içeren (<xref:System.Net.ServicePoint>s) içindeki <xref:System.AppDomain>.

## <a name="syntax"></a>Sözdizimi
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable` Alandır özel ve kodunuzda doğrudan kullanılmak üzere yüksetlmesi.
> 
> Microsoft hiçbir koşulda bir üretim uygulamasında bu alan kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Namespace:** <xref:System.Net>

**Derleme:** sisteminde (System.dll)

**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.
