---
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
ms.openlocfilehash: ed2b970d07df2c338870b386e75c1688703f1d68
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990426"
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
