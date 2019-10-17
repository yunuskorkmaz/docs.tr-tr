---
title: SqlStreamChars. SetLength (Int64) yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 291d6e9395581f2370dafc728521a314d54a686d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395720"
---
# <a name="sqlstreamcharssetlengthint64-method"></a>SqlStreamChars. SetLength (Int64) yöntemi

Türetilmiş bir sınıfta geçersiz kılınırsa, akış tarafından kullanılan kaynakları serbest bırakır. Bu yöntemi içeren derlemenin SQLAccess. dll ile bir arkadaş ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a>Parametreler

`value`\
Geçerli akışın bayt cinsinden istenen uzunluğu.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> @No__t-0 Yöntemi özeldir ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
