---
title: Bağlantı sınıfı
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 6f0b8902-f31c-4ab9-a8c9-de43228995ec
author: guardrex
ms.author: mairaw
ms.openlocfilehash: ed1fce1d16f9ddbe3a3ede91fecb1a3ca6b3d407
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146543"
---
# <a name="connection-class"></a><span data-ttu-id="d0496-102">Bağlantı sınıfı</span><span class="sxs-lookup"><span data-stu-id="d0496-102">Connection Class</span></span>

<span data-ttu-id="d0496-103">`Connection` Sınıfı ayrıştırıyor sunucu yanıtları, sıra isteklerini ve işlem hattı istekleri.</span><span class="sxs-lookup"><span data-stu-id="d0496-103">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0496-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0496-104">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="d0496-105">`Connection` Sınıfı dahili kullanım içindir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="d0496-105">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="d0496-106">Microsoft hiçbir koşulda, bir üretim uygulamasında bu sınıfın kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d0496-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0496-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0496-107">Requirements</span></span>

<span data-ttu-id="d0496-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="d0496-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="d0496-109">**Derleme:** Sistemde (System.dll)</span><span class="sxs-lookup"><span data-stu-id="d0496-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="d0496-110">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0496-110">**.NET Framework versions:** Available since 2.0.</span></span>
