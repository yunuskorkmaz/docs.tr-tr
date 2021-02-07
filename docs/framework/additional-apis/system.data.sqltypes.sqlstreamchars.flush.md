---
description: ': SqlStreamChars. Flush yöntemi hakkında daha fazla bilgi'
title: SqlStreamChars. Flush yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 8f519ffb8248a17608319eb0fbfe598f9ee3487a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684470"
---
# <a name="sqlstreamcharsflush-method"></a>SqlStreamChars. Flush yöntemi

Türetilmiş bir sınıfta geçersiz kılınırsa, bu akış için tüm arabellekleri temizler ve arabelleğe alınan verilerin temeldeki cihaza yazılmasına neden olur. Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

## <a name="syntax"></a>Syntax

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SqlStreamChars.Flush`Yöntemi özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System.Data.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
