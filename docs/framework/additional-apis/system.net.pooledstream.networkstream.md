---
title: PooledStream. NetworkStream özelliği (System.Net)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.PooledStream.NetworkStream
- System.Net.PooledStream.get_NetworkStream
- System.Net.PooledStream.set_NetworkStream
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 541b8c94b30675c1286b48a2291c3bd3e4aeea0b
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847180"
---
# <a name="pooledstreamnetworkstream-property"></a>PooledStream. NetworkStream özelliği

`PooledStream` soketi için ağ akışını alır veya ayarlar.

## <a name="syntax"></a>Sözdizimi

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a>Özellik değeri

<xref:System.Net.Sockets.NetworkStream>  
`PooledStream` soketi için ağ akışı.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `PooledStream.NetworkStream` özelliği Dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System. dll içinde)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
