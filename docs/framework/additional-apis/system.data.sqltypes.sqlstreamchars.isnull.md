---
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
ms.openlocfilehash: d80f653724b3ef0a1cadb69a5f72b1d9455597d6
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395741"
---
# <a name="sqlstreamcharsisnull-property"></a>SqlStreamChars. IsNull Özelliği

Türetilmiş bir sınıfta geçersiz kılındığında, akışın `null` olup olmadığını gösteren bir değer alır. Bu özelliği içeren derlemenin SQLAccess. dll ile bir Friend ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

## <a name="syntax"></a>Sözdizimi

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a>Özellik değeri

<xref:System.Boolean>\
akış `null` ise `true`; Aksi takdirde, `false`.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> @No__t-0 özelliği özeldir ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
