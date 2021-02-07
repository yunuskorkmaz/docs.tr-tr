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
# <a name="pooledstreamnetworkstream-property"></a><span data-ttu-id="93966-103">PooledStream. NetworkStream özelliği</span><span class="sxs-lookup"><span data-stu-id="93966-103">PooledStream.NetworkStream Property</span></span>

<span data-ttu-id="93966-104">Yuva için ağ akışını alır veya ayarlar `PooledStream` .</span><span class="sxs-lookup"><span data-stu-id="93966-104">Gets or sets the network stream for the `PooledStream` socket.</span></span>

## <a name="syntax"></a><span data-ttu-id="93966-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="93966-105">Syntax</span></span>

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="93966-106">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="93966-106">Property value</span></span>

<xref:System.Net.Sockets.NetworkStream>  
<span data-ttu-id="93966-107">Yuva için ağ akışı `PooledStream` .</span><span class="sxs-lookup"><span data-stu-id="93966-107">The network stream for the `PooledStream` socket.</span></span>

## <a name="remarks"></a><span data-ttu-id="93966-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93966-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="93966-109">`PooledStream.NetworkStream`Özelliği Dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="93966-109">The `PooledStream.NetworkStream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="93966-110">Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="93966-110">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="93966-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93966-111">Requirements</span></span>

<span data-ttu-id="93966-112">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="93966-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="93966-113">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="93966-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="93966-114">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="93966-114">**.NET Framework versions:** Available since 2.0.</span></span>
