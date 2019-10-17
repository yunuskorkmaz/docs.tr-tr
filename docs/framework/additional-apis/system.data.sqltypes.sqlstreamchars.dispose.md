---
title: SqlStreamChars. Dispose (Boolean) yöntemi (System. Data. SqlTypes)
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
ms.openlocfilehash: 44dc97835b8a7141064e8de4d2d5325c40be5a34
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395760"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a>SqlStreamChars. Dispose (Boolean) yöntemi

Türetilmiş bir sınıfta geçersiz kılınırsa, akış tarafından kullanılan kaynakları serbest bırakır. Bu yöntemi içeren derlemenin SQLAccess. dll ile bir arkadaş ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a>Parametreler

`disposing`\
hem yönetilen hem de yönetilmeyen kaynakları serbest bırakmak için 0 @no__t; yalnızca yönetilmeyen kaynakları serbest bırakmak için `false`.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> @No__t-0 Yöntemi özeldir ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
