---
description: ': SqlStreamChars. CanSeek özelliği hakkında daha fazla bilgi'
title: SqlStreamChars. CanSeek özelliği (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 5919a66bef9ac31e0ef15ad4af64b456700605f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802625"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="7af55-103">SqlStreamChars. CanSeek özelliği</span><span class="sxs-lookup"><span data-stu-id="7af55-103">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="7af55-104">Türetilmiş bir sınıfta geçersiz kılındığında, geçerli Buhar 'un arama işlemini destekleyip desteklemediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="7af55-104">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="7af55-105">Bu özelliği içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="7af55-105">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="7af55-106">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7af55-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="7af55-107">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7af55-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="7af55-108">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="7af55-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="7af55-109">`true` geçerli Buhar, arama işlemini destekliyorsa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="7af55-109">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="7af55-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7af55-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="7af55-111">`SqlStreamChars.CanSeek`Özelliği özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="7af55-111">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="7af55-112">Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7af55-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="7af55-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7af55-113">Requirements</span></span>

<span data-ttu-id="7af55-114">**Ad alanı:**<xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="7af55-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="7af55-115">**Bütünleştirilmiş kod:** System. Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="7af55-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="7af55-116">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7af55-116">**.NET Framework versions:** Available since 2.0.</span></span>
