---
description: ': SqlStreamChars. Close yöntemi hakkında daha fazla bilgi'
title: SqlStreamChars. Close yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 27f2ea6e288d166f3b63979a83a1cf80eeced334
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782383"
---
# <a name="sqlstreamcharsclose-method"></a>SqlStreamChars. Close yöntemi

Geçerli akışı kapatır ve akışla ilişkili tüm sistem kaynaklarını serbest bırakır. Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır. SQL Server tarafından kullanılmak üzere tasarlanmıştır. Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.

```csharp
public virtual void Close ();
```

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SqlStreamChars.Close`Yöntemi özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Data.SqlTypes>

**Bütünleştirilmiş kod:** System. Data (System.Data.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
