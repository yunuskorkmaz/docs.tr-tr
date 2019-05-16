---
title: SqlStreamChars.CanSeek özelliği (System.Data.SqlTypes)
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
ms.openlocfilehash: b85e21c6bc89d2a00ff8d302f67a3d074d5e7b8f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634383"
---
# <a name="sqlstreamcharscanseek-property"></a>SqlStreamChars.CanSeek Property

Türetilen bir sınıfta geçersiz kılındığında, geçerli akışı arama işlemini destekleyip desteklemediğini belirten bir değer alır. Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır. Bu, SQL Server tarafından kullanıma yöneliktir. Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>Özellik değeri

<xref:System.Boolean>\
`true` Geçerli akışı arama işlemini destekliyorsa, Aksi takdirde, `false`.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SqlStreamChars.CanSeek` Özelliği özeldir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.
>
> Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Namespace:** <xref:System.Data.SqlTypes>

**Derleme:** System.Data (içinde System.Data.dll)

**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.
