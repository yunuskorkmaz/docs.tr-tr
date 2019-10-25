---
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
ms.openlocfilehash: 6983ac071dad29b240308031ecd0a3562a6856e4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847201"
---
# <a name="sslstatesslprotocol-property"></a>SslState. SslProtocol özelliği

SSL protokolü sürümlerini alır.

## <a name="syntax"></a>Sözdizimi

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a>Özellik değeri

<xref:System.Security.Authentication.SslProtocols>  
SSL protokolü sürümlerini belirten numaralandırma değerlerinin bit düzeyinde birleşimi.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `SslState.SslProtocol` özelliği Dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.Net.Security>

**Bütünleştirilmiş kod:** Sistem (System. dll içinde)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
