---
description: ': SslState. SslProtocol özelliği hakkında daha fazla bilgi edinin'
title: SslState. SslProtocol özelliği (System .net. Security)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Security.SslState.SslProtocol
- System.Net.Security.SslState.get_SslProtocol
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: b0b9bebf23fcd8d643d06f1cff10c260c77a7c08
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699629"
---
# <a name="sslstatesslprotocol-property"></a>SslState. SslProtocol özelliği

SSL protokolü sürümlerini alır.

## <a name="syntax"></a>Syntax

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a>Özellik değeri

<xref:System.Security.Authentication.SslProtocols>  
SSL protokolü sürümlerini belirten numaralandırma değerlerinin bit düzeyinde birleşimi.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SslState.SslProtocol`Özelliği Dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net.Security>

**Bütünleştirilmiş kod:** Sistem (System.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
