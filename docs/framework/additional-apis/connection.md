---
title: Connection Sınıfı
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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675461"
---
# <a name="connection-class"></a><span data-ttu-id="7f9aa-102">Connection Sınıfı</span><span class="sxs-lookup"><span data-stu-id="7f9aa-102">Connection Class</span></span>

<span data-ttu-id="7f9aa-103">`Connection` Sınıfı ayrıştırıyor sunucu yanıtları, sıra isteklerini ve işlem hattı istekleri.</span><span class="sxs-lookup"><span data-stu-id="7f9aa-103">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="7f9aa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f9aa-104">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="7f9aa-105">`Connection` Sınıfı dahili kullanım içindir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="7f9aa-105">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="7f9aa-106">Microsoft hiçbir koşulda, bir üretim uygulamasında bu sınıfın kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7f9aa-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="7f9aa-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f9aa-107">Requirements</span></span>

<span data-ttu-id="7f9aa-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="7f9aa-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="7f9aa-109">**Derleme:** Sistemde (System.dll)</span><span class="sxs-lookup"><span data-stu-id="7f9aa-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="7f9aa-110">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7f9aa-110">**.NET Framework versions:** Available since 2.0.</span></span>
