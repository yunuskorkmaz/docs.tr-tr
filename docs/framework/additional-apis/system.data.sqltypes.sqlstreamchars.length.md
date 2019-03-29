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
ms.openlocfilehash: c2ef66fa493512e1fa062e22858ea251ced39453
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634147"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="d2eb4-102">SqlStreamChars.Length özelliği</span><span class="sxs-lookup"><span data-stu-id="d2eb4-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="d2eb4-103">Türetilen bir sınıfta geçersiz kılındığında, geçerli akış uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="d2eb4-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="d2eb4-104">Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="d2eb4-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="d2eb4-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="d2eb4-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="d2eb4-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2eb4-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2eb4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2eb4-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="d2eb4-108">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="d2eb4-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="d2eb4-109">Akışın uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="d2eb4-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2eb4-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2eb4-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d2eb4-111">`SqlStreamChars.Length` Özelliği özeldir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="d2eb4-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d2eb4-112">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d2eb4-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2eb4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2eb4-113">Requirements</span></span>

<span data-ttu-id="d2eb4-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="d2eb4-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="d2eb4-115">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="d2eb4-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="d2eb4-116">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2eb4-116">**.NET Framework versions:** Available since 2.0.</span></span>