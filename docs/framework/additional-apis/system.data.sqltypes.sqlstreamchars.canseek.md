---
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
ms.openlocfilehash: eb32978f62b7d46f0abf715e2bca347592c0fda8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395772"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="45e6e-102">SqlStreamChars. CanSeek özelliği</span><span class="sxs-lookup"><span data-stu-id="45e6e-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="45e6e-103">Türetilmiş bir sınıfta geçersiz kılındığında, geçerli Buhar 'un arama işlemini destekleyip desteklemediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="45e6e-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="45e6e-104">Bu özelliği içeren derlemenin SQLAccess. dll ile bir Friend ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="45e6e-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="45e6e-105">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="45e6e-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="45e6e-106">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="45e6e-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="45e6e-107">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="45e6e-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="45e6e-108">geçerli sözcük arama işlemini destekliyorsa, `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="45e6e-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="45e6e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45e6e-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="45e6e-110">@No__t-0 özelliği özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="45e6e-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="45e6e-111">Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="45e6e-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="45e6e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45e6e-112">Requirements</span></span>

<span data-ttu-id="45e6e-113">**Ad alanı:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="45e6e-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="45e6e-114">**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)</span><span class="sxs-lookup"><span data-stu-id="45e6e-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="45e6e-115">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45e6e-115">**.NET Framework versions:** Available since 2.0.</span></span>
