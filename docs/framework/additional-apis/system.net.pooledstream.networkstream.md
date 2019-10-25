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
# <a name="pooledstreamnetworkstream-property"></a><span data-ttu-id="548b3-102">PooledStream. NetworkStream özelliği</span><span class="sxs-lookup"><span data-stu-id="548b3-102">PooledStream.NetworkStream Property</span></span>

<span data-ttu-id="548b3-103">`PooledStream` soketi için ağ akışını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="548b3-103">Gets or sets the network stream for the `PooledStream` socket.</span></span>

## <a name="syntax"></a><span data-ttu-id="548b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="548b3-104">Syntax</span></span>

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="548b3-105">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="548b3-105">Property value</span></span>

<xref:System.Net.Sockets.NetworkStream>  
<span data-ttu-id="548b3-106">`PooledStream` soketi için ağ akışı.</span><span class="sxs-lookup"><span data-stu-id="548b3-106">The network stream for the `PooledStream` socket.</span></span>

## <a name="remarks"></a><span data-ttu-id="548b3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="548b3-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="548b3-108">`PooledStream.NetworkStream` özelliği Dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="548b3-108">The `PooledStream.NetworkStream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="548b3-109">Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="548b3-109">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="548b3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="548b3-110">Requirements</span></span>

<span data-ttu-id="548b3-111">**Ad alanı:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="548b3-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="548b3-112">**Bütünleştirilmiş kod:** Sistem (System. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="548b3-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="548b3-113">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="548b3-113">**.NET Framework versions:** Available since 2.0.</span></span>
