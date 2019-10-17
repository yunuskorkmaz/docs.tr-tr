---
title: SqlStreamChars. SetLength (Int64) yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 291d6e9395581f2370dafc728521a314d54a686d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395720"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="bd090-102">SqlStreamChars. SetLength (Int64) yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd090-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="bd090-103">Türetilmiş bir sınıfta geçersiz kılınırsa, akış tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="bd090-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="bd090-104">Bu yöntemi içeren derlemenin SQLAccess. dll ile bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="bd090-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="bd090-105">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bd090-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="bd090-106">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd090-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="bd090-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd090-107">Parameters</span></span>

`value`\
<span data-ttu-id="bd090-108">Geçerli akışın bayt cinsinden istenen uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="bd090-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd090-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd090-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="bd090-110">@No__t-0 Yöntemi özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bd090-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="bd090-111">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bd090-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd090-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd090-112">Requirements</span></span>

<span data-ttu-id="bd090-113">**Ad alanı:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="bd090-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="bd090-114">**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)</span><span class="sxs-lookup"><span data-stu-id="bd090-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="bd090-115">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bd090-115">**.NET Framework versions:** Available since 2.0.</span></span>
