---
description: ': SqlStreamChars. Flush yöntemi hakkında daha fazla bilgi'
title: SqlStreamChars. Flush yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 8f519ffb8248a17608319eb0fbfe598f9ee3487a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684470"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="14505-103">SqlStreamChars. Flush yöntemi</span><span class="sxs-lookup"><span data-stu-id="14505-103">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="14505-104">Türetilmiş bir sınıfta geçersiz kılınırsa, bu akış için tüm arabellekleri temizler ve arabelleğe alınan verilerin temeldeki cihaza yazılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="14505-104">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="14505-105">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="14505-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="14505-106">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="14505-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="14505-107">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="14505-107">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="14505-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="14505-108">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="14505-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14505-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="14505-110">`SqlStreamChars.Flush`Yöntemi özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="14505-110">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="14505-111">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="14505-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="14505-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14505-112">Requirements</span></span>

<span data-ttu-id="14505-113">**Ad alanı:**<xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="14505-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="14505-114">**Bütünleştirilmiş kod:** System. Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="14505-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="14505-115">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="14505-115">**.NET Framework versions:** Available since 2.0.</span></span>
