---
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
ms.openlocfilehash: 38ade5ce38cfe5003b2d06c0d8bb2db1a20bc05b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395620"
---
# <a name="sqlstreamcharsflush-method"></a>SqlStreamChars. Flush yöntemi

Türetilmiş bir sınıfta geçersiz kılınırsa, bu akış için tüm arabellekleri temizler ve arabelleğe alınan verilerin temeldeki cihaza yazılmasına neden olur. Bu yöntemi içeren derlemenin SQLAccess. dll ile bir arkadaş ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

## <a name="syntax"></a>Sözdizimi

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> @No__t-0 Yöntemi özeldir ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
