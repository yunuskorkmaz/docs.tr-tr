---
title: SqlStreamChars. Seek (Int64, SeekOrigin) yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: db8aba0a86c140ba62af8056011226532d415951
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395591"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a>SqlStreamChars. Seek (Int64, SeekOrigin) yöntemi

Türetilmiş bir sınıfta geçersiz kılınırsa, geçerli akış içindeki konumu ayarlar. Bu yöntemi içeren derlemenin SQLAccess. dll ile bir arkadaş ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a>Parametreler

`offset`\
@No__t-0 ile ilişkili bayt kayması.

`origin`\
Yeni konumun alınacağı başvuru noktasını gösteren sabit listesi değerlerinden biri.

## <a name="returns"></a>Döndürür

<xref:System.Int32>\
Geçerli akış içindeki yeni konum.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> @No__t-0 Yöntemi özeldir ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
