---
description: ': SqlStreamChars. Seek (Int64, SeekOrigin) yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 00f71aff95045d566b7932aec3f7e18259b4dfa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802573"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a>SqlStreamChars. Seek (Int64, SeekOrigin) yöntemi

Türetilmiş bir sınıfta geçersiz kılınırsa, geçerli akış içindeki konumu ayarlar. Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a>Parametreler

`offset`\
Öğesine göre bayt kayması `origin` .

`origin`\
Yeni konumun alınacağı başvuru noktasını gösteren sabit listesi değerlerinden biri.

## <a name="returns"></a>Döndürülenler

<xref:System.Int32>\
Geçerli akış içindeki yeni konum.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SqlStreamChars.Seek`Yöntemi özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System.Data.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
