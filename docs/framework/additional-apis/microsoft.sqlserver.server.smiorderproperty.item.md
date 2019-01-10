---
title: SmiOrderProperty.Item özelliği (Microsoft.SqlServer.Server)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c586d07e8ea0c2ac0b1efb603e8900d681fd0a91
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152220"
---
# <a name="smiorderpropertyitem-property"></a>SmiOrderProperty.Item özelliği

Varlık için sütun sırasını alır. Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır. Bu, SQL Server tarafından kullanıma yöneliktir. Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.

## <a name="syntax"></a>Sözdizimi

```csharp
internal SmiColumnOrder Item { get; }
```

## <a name="property-value"></a>Özellik değeri

Sütun sırası.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SmiOrderProperty.Item` Özelliği dahili kullanım içindir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.
>
> Microsoft hiçbir koşulda, bir üretim uygulamasında bu özelliğin kullanımı desteklemez.

## <a name="requirements"></a>Gereksinimler

**Namespace:** <xref:Microsoft.SqlServer.Server>

**Derleme:** System.Data (içinde System.Data.dll)

**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.