---
description: ': SqlStreamChars. Read (Char [], Int32, Int32) yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: a899ddff7b7242fcc32aaf7b7f7794970596027b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802586"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a>SqlStreamChars. Read (Char [], Int32, Int32) yöntemi

Türetilmiş bir sınıfta geçersiz kılınırsa, giriş akışından sonraki karakter kümesini okur. Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

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

## <a name="returns"></a>Döndürülenler

<xref:System.Int32>\
Arabelleğe okunan toplam karakter sayısı.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SqlStreamChars.Read`Yöntemi özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System.Data.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
