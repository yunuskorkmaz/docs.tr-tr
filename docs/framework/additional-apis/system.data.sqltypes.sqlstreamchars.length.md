---
description: ': SqlStreamChars. length özelliği hakkında daha fazla bilgi'
title: SqlStreamChars. length Özelliği (System. Data. SqlTypes)
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
ms.openlocfilehash: b0a9686cadc6d4018c7f291f0326b71195fd5cf5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802599"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="f0e7e-103">SqlStreamChars. length özelliği</span><span class="sxs-lookup"><span data-stu-id="f0e7e-103">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="f0e7e-104">Türetilmiş bir sınıfta geçersiz kılındığında, geçerli akışın uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="f0e7e-104">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="f0e7e-105">Bu özelliği içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="f0e7e-105">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="f0e7e-106">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f0e7e-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="f0e7e-107">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0e7e-107">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="f0e7e-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="f0e7e-108">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="f0e7e-109">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="f0e7e-109">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="f0e7e-110">Akışın uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="f0e7e-110">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="f0e7e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0e7e-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f0e7e-112">`SqlStreamChars.Length`Özelliği özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="f0e7e-112">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f0e7e-113">Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f0e7e-113">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0e7e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0e7e-114">Requirements</span></span>

<span data-ttu-id="f0e7e-115">**Ad alanı:**<xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="f0e7e-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="f0e7e-116">**Bütünleştirilmiş kod:** System. Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="f0e7e-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="f0e7e-117">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0e7e-117">**.NET Framework versions:** Available since 2.0.</span></span>
