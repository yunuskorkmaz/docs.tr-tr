---
description: ': SqlStreamChars. IsNull özelliği hakkında daha fazla bilgi'
title: SqlStreamChars. IsNull Özelliği (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: b1408a8ba9cd1c38f73d5fa6b818f441d6223bc8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791926"
---
# <a name="sqlstreamcharsisnull-property"></a>SqlStreamChars. IsNull Özelliği

Türetilmiş bir sınıfta geçersiz kılındığında akışın olup olmadığını gösteren bir değer alır `null` . Bu özelliği içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

## <a name="syntax"></a>Syntax

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a>Özellik değeri

<xref:System.Boolean>\
`true` Akış ise `null` , aksi durumda, `false` .

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SqlStreamChars.IsNull`Özelliği özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System.Data.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
