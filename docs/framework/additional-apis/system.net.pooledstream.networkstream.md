---
description: ': PooledStream. NetworkStream özelliği hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8a4f1d6bd9297028e763ef73bf96f85cbbfdafd6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699642"
---
# <a name="pooledstreamnetworkstream-property"></a>PooledStream. NetworkStream özelliği

Yuva için ağ akışını alır veya ayarlar `PooledStream` .

## <a name="syntax"></a>Syntax

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a>Özellik değeri

<xref:System.Net.Sockets.NetworkStream>  
Yuva için ağ akışı `PooledStream` .

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `PooledStream.NetworkStream`Özelliği Dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
