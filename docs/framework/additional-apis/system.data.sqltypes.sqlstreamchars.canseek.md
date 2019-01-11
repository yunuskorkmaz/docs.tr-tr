---
title: SqlStreamChars.CanSeek özelliği (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
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
ms.openlocfilehash: 8d7bd7fb90177932b413c379f618a6d36374de57
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223149"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="e80ca-102">SqlStreamChars.CanSeek özelliği</span><span class="sxs-lookup"><span data-stu-id="e80ca-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="e80ca-103">Türetilen bir sınıfta geçersiz kılındığında, geçerli akışı arama işlemini destekleyip desteklemediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e80ca-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="e80ca-104">Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="e80ca-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e80ca-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e80ca-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e80ca-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="e80ca-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="e80ca-107">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="e80ca-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="e80ca-108">`true` Geçerli akışı arama işlemini destekliyorsa, Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="e80ca-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e80ca-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e80ca-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e80ca-110">`SqlStreamChars.CanSeek` Özelliği özeldir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="e80ca-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e80ca-111">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e80ca-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e80ca-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e80ca-112">Requirements</span></span>

<span data-ttu-id="e80ca-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e80ca-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e80ca-114">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="e80ca-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e80ca-115">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e80ca-115">**.NET Framework versions:** Available since 2.0.</span></span>