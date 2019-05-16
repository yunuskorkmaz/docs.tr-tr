---
title: SqlStreamChars.Length özelliği (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 8f318f593237dc555d546858152bb03546c8306b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634448"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="b1ee8-102">SqlStreamChars.Length özelliği</span><span class="sxs-lookup"><span data-stu-id="b1ee8-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="b1ee8-103">Türetilen bir sınıfta geçersiz kılındığında, geçerli akış uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="b1ee8-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="b1ee8-104">Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="b1ee8-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="b1ee8-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b1ee8-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="b1ee8-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="b1ee8-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="b1ee8-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1ee8-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="b1ee8-108">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="b1ee8-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="b1ee8-109">Akışın uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="b1ee8-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1ee8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1ee8-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="b1ee8-111">`SqlStreamChars.Length` Özelliği özeldir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="b1ee8-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b1ee8-112">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b1ee8-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b1ee8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1ee8-113">Requirements</span></span>

<span data-ttu-id="b1ee8-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="b1ee8-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="b1ee8-115">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="b1ee8-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="b1ee8-116">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b1ee8-116">**.NET Framework versions:** Available since 2.0.</span></span>
