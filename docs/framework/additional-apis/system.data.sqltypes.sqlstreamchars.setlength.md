---
description: ': SqlStreamChars. SetLength (Int64) yöntemi hakkında daha fazla bilgi edinin'
title: SqlStreamChars. SetLength (Int64) yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d10ce55126ae09062fe895c3a686ce5d94174554
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804146"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="d96a7-103">SqlStreamChars. SetLength (Int64) yöntemi</span><span class="sxs-lookup"><span data-stu-id="d96a7-103">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="d96a7-104">Türetilmiş bir sınıfta geçersiz kılınırsa, akış tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="d96a7-104">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="d96a7-105">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="d96a7-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="d96a7-106">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d96a7-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="d96a7-107">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d96a7-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="d96a7-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d96a7-108">Parameters</span></span>

`value`\
<span data-ttu-id="d96a7-109">Geçerli akışın bayt cinsinden istenen uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="d96a7-109">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="d96a7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d96a7-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d96a7-111">`SqlStreamChars.SetLength`Yöntemi özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="d96a7-111">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d96a7-112">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d96a7-112">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d96a7-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d96a7-113">Requirements</span></span>

<span data-ttu-id="d96a7-114">**Ad alanı:**<xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="d96a7-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="d96a7-115">**Bütünleştirilmiş kod:** System. Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="d96a7-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="d96a7-116">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d96a7-116">**.NET Framework versions:** Available since 2.0.</span></span>
