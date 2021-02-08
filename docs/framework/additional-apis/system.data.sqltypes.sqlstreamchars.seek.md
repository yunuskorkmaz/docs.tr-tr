---
description: ': SqlStreamChars. Seek (Int64, SeekOrigin) yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 00f71aff95045d566b7932aec3f7e18259b4dfa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802573"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="875d0-103">SqlStreamChars. Seek (Int64, SeekOrigin) yöntemi</span><span class="sxs-lookup"><span data-stu-id="875d0-103">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="875d0-104">Türetilmiş bir sınıfta geçersiz kılınırsa, geçerli akış içindeki konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="875d0-104">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="875d0-105">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="875d0-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="875d0-106">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="875d0-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="875d0-107">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="875d0-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="875d0-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="875d0-108">Parameters</span></span>

`offset`\
<span data-ttu-id="875d0-109">Öğesine göre bayt kayması `origin` .</span><span class="sxs-lookup"><span data-stu-id="875d0-109">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="875d0-110">Yeni konumun alınacağı başvuru noktasını gösteren sabit listesi değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="875d0-110">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="875d0-111">Döndürülenler</span><span class="sxs-lookup"><span data-stu-id="875d0-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="875d0-112">Geçerli akış içindeki yeni konum.</span><span class="sxs-lookup"><span data-stu-id="875d0-112">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="875d0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="875d0-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="875d0-114">`SqlStreamChars.Seek`Yöntemi özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="875d0-114">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="875d0-115">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="875d0-115">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="875d0-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="875d0-116">Requirements</span></span>

<span data-ttu-id="875d0-117">**Ad alanı:**<xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="875d0-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="875d0-118">**Bütünleştirilmiş kod:** System. Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="875d0-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="875d0-119">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="875d0-119">**.NET Framework versions:** Available since 2.0.</span></span>
