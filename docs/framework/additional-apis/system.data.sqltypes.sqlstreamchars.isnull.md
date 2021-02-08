---
description: ': SqlStreamChars. IsNull özelliği hakkında daha fazla bilgi'
title: SqlStreamChars. IsNull Özelliği (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: b1408a8ba9cd1c38f73d5fa6b818f441d6223bc8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791926"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="0c1ef-103">SqlStreamChars. IsNull Özelliği</span><span class="sxs-lookup"><span data-stu-id="0c1ef-103">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="0c1ef-104">Türetilmiş bir sınıfta geçersiz kılındığında akışın olup olmadığını gösteren bir değer alır `null` .</span><span class="sxs-lookup"><span data-stu-id="0c1ef-104">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="0c1ef-105">Bu özelliği içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="0c1ef-105">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="0c1ef-106">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0c1ef-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="0c1ef-107">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c1ef-107">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c1ef-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="0c1ef-108">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="0c1ef-109">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="0c1ef-109">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="0c1ef-110">`true` Akış ise `null` , aksi durumda, `false` .</span><span class="sxs-lookup"><span data-stu-id="0c1ef-110">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c1ef-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c1ef-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="0c1ef-112">`SqlStreamChars.IsNull`Özelliği özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="0c1ef-112">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0c1ef-113">Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0c1ef-113">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0c1ef-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c1ef-114">Requirements</span></span>

<span data-ttu-id="0c1ef-115">**Ad alanı:**<xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="0c1ef-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="0c1ef-116">**Bütünleştirilmiş kod:** System. Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="0c1ef-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="0c1ef-117">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c1ef-117">**.NET Framework versions:** Available since 2.0.</span></span>
