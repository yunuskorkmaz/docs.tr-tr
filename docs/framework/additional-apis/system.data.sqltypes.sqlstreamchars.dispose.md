---
title: SqlStreamChars.Dispose(Boolean) yöntemi (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: cc8df68a608000d89dd322b0d396504483bbf372
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675162"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a>SqlStreamChars.Dispose(Boolean) yöntemi

Türetilen bir sınıfta geçersiz kılındığında, akış tarafından kullanılan kaynakları serbest bırakır. Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır. Bu, SQL Server tarafından kullanıma yöneliktir. Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a>Parametreler

`disposing`\
`true` hem yönetilen hem de yönetilmeyen kaynakları serbest bırakmak için; `false` yalnızca yönetilmeyen kaynaklar serbest bırakılacaksa.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SqlStreamChars.Dispose` Yöntemi private olduğuna ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.
>
> Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Namespace:** <xref:System.Data.SqlTypes>

**Derleme:** System.Data (içinde System.Data.dll)

**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.