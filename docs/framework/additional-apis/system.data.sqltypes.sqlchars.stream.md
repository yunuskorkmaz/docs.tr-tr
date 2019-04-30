---
title: SqlChars.Stream özelliği (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 4858d9f8878e5b56a0811edf92a2faa729775156
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675207"
---
# <a name="sqlcharsstream-property"></a>SqlChars.Stream Özelliği

Alır veya ayarlar karakter akışı. Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır. Bu, SQL Server tarafından kullanıma yöneliktir. Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a>Özellik değeri

`System.Data.SqlTypes.SqlStreamChars`\
Karakter akış.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SqlChars.Stream` Özelliği dahili kullanım içindir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.
>
> Microsoft hiçbir koşulda, bir üretim uygulamasında bu özelliğin kullanımı desteklemez.

## <a name="requirements"></a>Gereksinimler

**Namespace:** <xref:System.Data.SqlTypes>

**Derleme:** System.Data (içinde System.Data.dll)

**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.