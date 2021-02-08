---
description: 'Daha fazla bilgi edinin: ComNetOS sınıfı'
title: ComNetOS sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ComNetOS
- System.Net.ComNetOS.IsWin7orLater
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 7376fe4a5e02818907cb71573451fffb3a3667cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802534"
---
# <a name="comnetos-class"></a>ComNetOS sınıfı

Geçerli işletim sistemi hakkında, sürümü ve yükleme türü (istemci veya sunucu) gibi bilgiler sağlar. Bu sınıf devralınamaz.
  
```csharp  
internal static class ComNetOS
```

> [!WARNING]
> Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="iswin7orlater-field"></a>IsWin7orLater alanı

İşletim sistemi sürümünün Windows 7 veya sonraki bir sürümü olup olmadığını belirtir.

```csharp
internal static readonly bool IsWin7orLater
```

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System.dll)
