---
description: ': SqlStreamChars. CanSeek özelliği hakkında daha fazla bilgi'
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
ms.openlocfilehash: 5919a66bef9ac31e0ef15ad4af64b456700605f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802625"
---
# <a name="sqlstreamcharscanseek-property"></a>SqlStreamChars. CanSeek özelliği

Türetilmiş bir sınıfta geçersiz kılındığında, geçerli Buhar 'un arama işlemini destekleyip desteklemediğini gösteren bir değer alır. Bu özelliği içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>Özellik değeri

<xref:System.Boolean>\
`true` geçerli Buhar, arama işlemini destekliyorsa; Aksi takdirde, `false` .

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SqlStreamChars.CanSeek`Özelliği özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System.Data.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
