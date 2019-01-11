---
title: SmiOrderProperty.Item özelliği (Microsoft.SqlServer.Server)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 5453167e16e2658b3546b7114201b04d481a0c79
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223020"
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