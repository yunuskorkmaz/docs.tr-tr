---
title: Bağlantı sınıfı (System.Net)
description: .NET 'teki bağlantı sınıfı hakkında bilgi edinin. Bu sınıf sunucu yanıtlarını, kuyruk isteklerini ve işlem hattı isteklerini ayrıştırır. System.NET ad alanıdır.
ms.date: 05/01/2017
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Connection
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 6f0b8902-f31c-4ab9-a8c9-de43228995ec
ms.openlocfilehash: cb28724ed782fc5395dc74e9c59249ebdea44ddf
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989825"
---
# <a name="connection-class"></a><span data-ttu-id="0c6c5-105">Connection Sınıfı</span><span class="sxs-lookup"><span data-stu-id="0c6c5-105">Connection Class</span></span>

<span data-ttu-id="0c6c5-106">`Connection`Sınıfı sunucu yanıtlarını, kuyruk isteklerini ve işlem hattı isteklerini ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="0c6c5-106">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c6c5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="0c6c5-107">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="0c6c5-108">`Connection`Sınıfı dahili ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="0c6c5-108">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0c6c5-109">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0c6c5-109">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0c6c5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c6c5-110">Requirements</span></span>

<span data-ttu-id="0c6c5-111">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="0c6c5-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="0c6c5-112">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="0c6c5-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="0c6c5-113">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c6c5-113">**.NET Framework versions:** Available since 2.0.</span></span>
