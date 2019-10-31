---
title: ServicePointManager. s_ServicePointTable alanı
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68445f4a290b9f4fe2696e35cda391b6c0ee8f85
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119994"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>ServicePointManager. s\_ServicePointTable alanı

`ServicePointManager.s_ServicePointTable`, <xref:System.AppDomain>içindeki etkin HTTP bağlantılarının (<xref:System.Net.ServicePoint>s) listesini içeren bir <xref:System.Collections.Hashtable>.

## <a name="syntax"></a>Sözdizimi
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable` alanı özeldir ve doğrudan kodunuzda kullanılmamalıdır.
> 
> Microsoft, herhangi bir koşulda bu alanın bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System. dll içinde)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
