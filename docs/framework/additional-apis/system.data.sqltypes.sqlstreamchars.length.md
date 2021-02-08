---
description: ': SqlStreamChars. length özelliği hakkında daha fazla bilgi'
title: SqlStreamChars. length Özelliği (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: b0a9686cadc6d4018c7f291f0326b71195fd5cf5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802599"
---
# <a name="sqlstreamcharslength-property"></a>SqlStreamChars. length özelliği

Türetilmiş bir sınıfta geçersiz kılındığında, geçerli akışın uzunluğunu alır. Bu özelliği içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

## <a name="syntax"></a>Syntax

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a>Özellik değeri

<xref:System.Int64>\
Akışın uzunluğu.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SqlStreamChars.Length`Özelliği özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System.Data.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
