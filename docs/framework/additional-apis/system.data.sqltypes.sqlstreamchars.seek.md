---
title: SqlStreamChars. Seek (Int64, SeekOrigin) yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: db8aba0a86c140ba62af8056011226532d415951
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395591"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="e66a5-102">SqlStreamChars. Seek (Int64, SeekOrigin) yöntemi</span><span class="sxs-lookup"><span data-stu-id="e66a5-102">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="e66a5-103">Türetilmiş bir sınıfta geçersiz kılınırsa, geçerli akış içindeki konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e66a5-103">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="e66a5-104">Bu yöntemi içeren derlemenin SQLAccess. dll ile bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="e66a5-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e66a5-105">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e66a5-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e66a5-106">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e66a5-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="e66a5-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e66a5-107">Parameters</span></span>

`offset`\
<span data-ttu-id="e66a5-108">@No__t-0 ile ilişkili bayt kayması.</span><span class="sxs-lookup"><span data-stu-id="e66a5-108">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="e66a5-109">Yeni konumun alınacağı başvuru noktasını gösteren sabit listesi değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="e66a5-109">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="e66a5-110">Döndürür</span><span class="sxs-lookup"><span data-stu-id="e66a5-110">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="e66a5-111">Geçerli akış içindeki yeni konum.</span><span class="sxs-lookup"><span data-stu-id="e66a5-111">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="e66a5-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e66a5-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e66a5-113">@No__t-0 Yöntemi özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e66a5-113">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e66a5-114">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e66a5-114">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e66a5-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e66a5-115">Requirements</span></span>

<span data-ttu-id="e66a5-116">**Ad alanı:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e66a5-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e66a5-117">**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)</span><span class="sxs-lookup"><span data-stu-id="e66a5-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e66a5-118">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e66a5-118">**.NET Framework versions:** Available since 2.0.</span></span>
