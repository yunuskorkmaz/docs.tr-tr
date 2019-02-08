---
title: SqlStreamChars.CanSeek özelliği (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: bde4764af9d0160997dc202f722a12393cfa59c1
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826856"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="2c8ca-102">SqlStreamChars.CanSeek Property</span><span class="sxs-lookup"><span data-stu-id="2c8ca-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="2c8ca-103">Türetilen bir sınıfta geçersiz kılındığında, geçerli akışı arama işlemini destekleyip desteklemediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="2c8ca-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="2c8ca-104">Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="2c8ca-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="2c8ca-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="2c8ca-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="2c8ca-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c8ca-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="2c8ca-107">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="2c8ca-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="2c8ca-108">`true` Geçerli akışı arama işlemini destekliyorsa, Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="2c8ca-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c8ca-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c8ca-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="2c8ca-110">`SqlStreamChars.CanSeek` Özelliği özeldir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="2c8ca-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="2c8ca-111">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2c8ca-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="2c8ca-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c8ca-112">Requirements</span></span>

<span data-ttu-id="2c8ca-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="2c8ca-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="2c8ca-114">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="2c8ca-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="2c8ca-115">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2c8ca-115">**.NET Framework versions:** Available since 2.0.</span></span>