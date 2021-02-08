---
description: 'Daha fazla bilgi edinin: HttpStatusDescription sınıfı'
title: HttpStatusDescription sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fa135a6421397ce6b7be2af05d66aa8e81beafb7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802508"
---
# <a name="httpstatusdescription-class"></a>HttpStatusDescription sınıfı

Standart HTTP durum açıklamalarını sağlar. Bu sınıf devralınamaz.

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="get-method"></a>Get yöntemi

Belirtilen HTTP durum koduyla ilişkili açıklamayı döndürür.

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a>Parametreler

`code` <xref:System.Int32>

HTTP durum kodu, örneğin, `404` .

### <a name="return-value"></a>Döndürülen değer

<xref:System.String?displayProperty=nameWithType>

HTTP durum açıklaması.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System.dll)
