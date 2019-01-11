---
title: SqlStreamChars.CanSeek özelliği (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 8d7bd7fb90177932b413c379f618a6d36374de57
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223149"
---
# <a name="sqlstreamcharscanseek-property"></a>SqlStreamChars.CanSeek özelliği

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