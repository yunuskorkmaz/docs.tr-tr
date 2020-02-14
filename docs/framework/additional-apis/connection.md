---
title: Bağlantı sınıfı (System.Net)
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
ms.openlocfilehash: e9e0f4eed5eb4a7efd27177ab65551afa87fb7f6
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215086"
---
# <a name="connection-class"></a><span data-ttu-id="c4e56-102">Connection Sınıfı</span><span class="sxs-lookup"><span data-stu-id="c4e56-102">Connection Class</span></span>

<span data-ttu-id="c4e56-103">`Connection` sınıfı sunucu yanıtlarını, kuyruk isteklerini ve işlem hattı isteklerini ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="c4e56-103">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="c4e56-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4e56-104">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="c4e56-105">`Connection` sınıfı dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4e56-105">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="c4e56-106">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c4e56-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c4e56-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4e56-107">Requirements</span></span>

<span data-ttu-id="c4e56-108">**Ad alanı:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="c4e56-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="c4e56-109">**Bütünleştirilmiş kod:** Sistem (System. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="c4e56-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="c4e56-110">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4e56-110">**.NET Framework versions:** Available since 2.0.</span></span>
