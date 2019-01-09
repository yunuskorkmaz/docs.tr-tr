---
title: SqlStreamChars.IsNull özelliği (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 79ebb9ec54185a94cb95dfd0fb2929e61cf513ef
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152208"
---
# <a name="sqlstreamcharsisnull-property"></a>SqlStreamChars.IsNull özelliği

Türetilen bir sınıfta geçersiz kılındığında, akış olup olmadığını belirten bir değer alır `null`. Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır. Bu, SQL Server tarafından kullanıma yöneliktir. Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.

## <a name="syntax"></a>Sözdizimi

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a>Özellik değeri

<xref:System.Boolean>\
`true` Akış ise `null`; Aksi takdirde `false`.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SqlStreamChars.IsNull` Özelliği özeldir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.
>
> Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Namespace:** <xref:System.Data.SqlTypes>

**Derleme:** System.Data (içinde System.Data.dll)

**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.