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
ms.openlocfilehash: ebcf5c3f13b3bd30a8e091be09ae546eee1eaffe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675448"
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable alan

`ServicePointManager.s_ServicePointTable` olan bir <xref:System.Collections.Hashtable> etkin HTTP bağlantıları listesini içeren (<xref:System.Net.ServicePoint>s) içindeki <xref:System.AppDomain>.

## <a name="syntax"></a>Sözdizimi
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable` Alan özeldir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.
> 
> Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Namespace:** <xref:System.Net>

**Derleme:** Sistemde (System.dll)

**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.
