---
title: SqlStreamChars. Dispose (Boolean) yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 44dc97835b8a7141064e8de4d2d5325c40be5a34
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395760"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="595ce-102">SqlStreamChars. Dispose (Boolean) yöntemi</span><span class="sxs-lookup"><span data-stu-id="595ce-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="595ce-103">Türetilmiş bir sınıfta geçersiz kılınırsa, akış tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="595ce-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="595ce-104">Bu yöntemi içeren derlemenin SQLAccess. dll ile bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="595ce-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="595ce-105">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="595ce-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="595ce-106">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="595ce-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="595ce-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="595ce-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="595ce-108">hem yönetilen hem de yönetilmeyen kaynakları serbest bırakmak için `true`; yalnızca yönetilmeyen kaynakları serbest bırakmak için `false`.</span><span class="sxs-lookup"><span data-stu-id="595ce-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="595ce-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="595ce-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="595ce-110">`SqlStreamChars.Dispose` Yöntemi özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="595ce-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="595ce-111">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="595ce-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="595ce-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="595ce-112">Requirements</span></span>

<span data-ttu-id="595ce-113">**Ad alanı:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="595ce-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="595ce-114">**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)</span><span class="sxs-lookup"><span data-stu-id="595ce-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="595ce-115">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="595ce-115">**.NET Framework versions:** Available since 2.0.</span></span>
