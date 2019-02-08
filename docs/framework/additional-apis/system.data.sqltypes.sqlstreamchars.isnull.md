---
title: SqlStreamChars.IsNull Property (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 7d2a2cf66ce2a375b1e5989b2fb6ddc9e3d94411
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825452"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="4093b-102">SqlStreamChars.IsNull Property</span><span class="sxs-lookup"><span data-stu-id="4093b-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="4093b-103">Türetilen bir sınıfta geçersiz kılındığında, akış olup olmadığını belirten bir değer alır `null`.</span><span class="sxs-lookup"><span data-stu-id="4093b-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="4093b-104">Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="4093b-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="4093b-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="4093b-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="4093b-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="4093b-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="4093b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4093b-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="4093b-108">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="4093b-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="4093b-109">`true` Akış ise `null`; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="4093b-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4093b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4093b-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="4093b-111">`SqlStreamChars.IsNull` Özelliği özeldir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="4093b-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="4093b-112">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4093b-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="4093b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4093b-113">Requirements</span></span>

<span data-ttu-id="4093b-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="4093b-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="4093b-115">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="4093b-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="4093b-116">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4093b-116">**.NET Framework versions:** Available since 2.0.</span></span>