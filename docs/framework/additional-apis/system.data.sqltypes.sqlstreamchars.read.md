---
title: SqlStreamChars. Read (Char [], Int32, Int32) yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9c8a1526e75fdc304022e74a7cc52506762489ea
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395746"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a>SqlStreamChars. Read (Char [], Int32, Int32) yöntemi

Türetilmiş bir sınıfta geçersiz kılınırsa, giriş akışından sonraki karakter kümesini okur. Bu yöntemi içeren derlemenin SQLAccess. dll ile bir arkadaş ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>Parametreler

`buffer`\
Okunacak bir Char dizisi.

`offset`\
Kaynağa göre bir göreli konum.

`count`\
Geçerli akıştan okunacak karakter sayısı.

## <a name="returns"></a>Döndürür

<xref:System.Int32>\
Arabelleğe okunan toplam karakter sayısı.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> @No__t-0 Yöntemi özeldir ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
