---
title: ServicePointManager.s_ServicePointTable Alanı
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
ms.openlocfilehash: 6a56ecd6fc85005f5987c3c2ad0d1680ca63c398
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155825"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>ServicePointManager.s\_ServicePointTable Alanı

`ServicePointManager.s_ServicePointTable`etkin <xref:System.Collections.Hashtable> HTTP bağlantılarının (lar)<xref:System.Net.ServicePoint>listesini içeren bir <xref:System.AppDomain>bağlantıdır.

## <a name="syntax"></a>Sözdizimi
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> Alan `ServicePointManager.s_ServicePointTable` özeldir ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, hiçbir koşulda bir üretim uygulamasında bu alanın kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net>

**Montaj:** Sistem (System.dll'de)

**.NET Framework sürümleri:** 2.0'dan beri mevcuttur.
