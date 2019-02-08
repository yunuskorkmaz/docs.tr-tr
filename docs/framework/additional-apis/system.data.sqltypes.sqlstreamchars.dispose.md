---
title: SqlStreamChars.Dispose(Boolean) yöntemi (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 4e6cfd6d4c04b1a2835b6e34b82c95b564dea588
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826869"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="b40cd-102">SqlStreamChars.Dispose(Boolean) yöntemi</span><span class="sxs-lookup"><span data-stu-id="b40cd-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="b40cd-103">Türetilen bir sınıfta geçersiz kılındığında, akış tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="b40cd-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="b40cd-104">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="b40cd-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="b40cd-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b40cd-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="b40cd-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="b40cd-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="b40cd-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b40cd-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="b40cd-108">`true` hem yönetilen hem de yönetilmeyen kaynakları serbest bırakmak için; `false` yalnızca yönetilmeyen kaynaklar serbest bırakılacaksa.</span><span class="sxs-lookup"><span data-stu-id="b40cd-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="b40cd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b40cd-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="b40cd-110">`SqlStreamChars.Dispose` Yöntemi private olduğuna ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="b40cd-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b40cd-111">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b40cd-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b40cd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b40cd-112">Requirements</span></span>

<span data-ttu-id="b40cd-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="b40cd-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="b40cd-114">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="b40cd-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="b40cd-115">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b40cd-115">**.NET Framework versions:** Available since 2.0.</span></span>