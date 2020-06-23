---
title: ServicePointManager. s_ServicePointTable alanı
description: .NET 'teki ServicePointManager. s_ServicePointTable alanı hakkında bilgi edinin. Bu karma tablo alanı AppDomain 'de etkin HTTP bağlantıları (ServicePoints) içerir.
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
ms.openlocfilehash: 9462ae10125dd37706f786a1f2cef78e62fbabcc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989548"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>ServicePointManager. s \_ servicepointtable alanı

`ServicePointManager.s_ServicePointTable`<xref:System.Collections.Hashtable>, içindeki ETKIN HTTP bağlantılarının listesini içeren bir <xref:System.Net.ServicePoint> ' dır <xref:System.AppDomain> .

## <a name="syntax"></a>Syntax
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable`Alan özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Microsoft, herhangi bir koşulda bu alanın bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
