---
title: ServicePointManager. CloseConnectionGroups yöntemi (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.CloseConnectionGroups
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: aae9a389ae35e249d43c9dc830a68ec32cf4afef
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990364"
---
# <a name="servicepointmanagercloseconnectiongroups-method"></a>ServicePointManager. CloseConnectionGroups yöntemi

Tüm hizmet noktalarında dolaşır ve belirtilen ada sahip bağlantı gruplarını kapatır.

```csharp
internal static void CloseConnectionGroups(string connectionGroupName)
```

> [!WARNING]
> Bu yöntem dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="parameters"></a>Parametreler

`connectionGroupName` <xref:System.String>

Kapatılacak bağlantı grubunun adı.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System.dll)
