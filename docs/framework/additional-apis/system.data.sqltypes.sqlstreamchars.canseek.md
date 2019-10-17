---
title: SqlStreamChars. CanSeek özelliği (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: eb32978f62b7d46f0abf715e2bca347592c0fda8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395772"
---
# <a name="sqlstreamcharscanseek-property"></a>SqlStreamChars. CanSeek özelliği

Türetilmiş bir sınıfta geçersiz kılındığında, geçerli Buhar 'un arama işlemini destekleyip desteklemediğini gösteren bir değer alır. Bu özelliği içeren derlemenin SQLAccess. dll ile bir Friend ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>Özellik değeri

<xref:System.Boolean>\
geçerli sözcük arama işlemini destekliyorsa, `true`; Aksi takdirde, `false`.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> @No__t-0 özelliği özeldir ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
