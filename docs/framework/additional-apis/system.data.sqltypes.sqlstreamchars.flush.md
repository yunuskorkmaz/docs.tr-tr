---
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
ms.openlocfilehash: 38ade5ce38cfe5003b2d06c0d8bb2db1a20bc05b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395620"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="174b4-102">SqlStreamChars. Flush yöntemi</span><span class="sxs-lookup"><span data-stu-id="174b4-102">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="174b4-103">Türetilmiş bir sınıfta geçersiz kılınırsa, bu akış için tüm arabellekleri temizler ve arabelleğe alınan verilerin temeldeki cihaza yazılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="174b4-103">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="174b4-104">Bu yöntemi içeren derlemenin SQLAccess. dll ile bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="174b4-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="174b4-105">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="174b4-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="174b4-106">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="174b4-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="174b4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="174b4-107">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="174b4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="174b4-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="174b4-109">@No__t-0 Yöntemi özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="174b4-109">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="174b4-110">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="174b4-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="174b4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="174b4-111">Requirements</span></span>

<span data-ttu-id="174b4-112">**Ad alanı:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="174b4-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="174b4-113">**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)</span><span class="sxs-lookup"><span data-stu-id="174b4-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="174b4-114">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="174b4-114">**.NET Framework versions:** Available since 2.0.</span></span>
