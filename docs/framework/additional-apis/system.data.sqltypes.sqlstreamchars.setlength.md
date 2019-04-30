---
title: SqlStreamChars.SetLength(Int64) yöntemi (System.Data.SqlTypes)
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
ms.openlocfilehash: 1283fea83cf77bbc898d460feedc72b898a65fb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675182"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="903d6-102">SqlStreamChars.SetLength(Int64) yöntemi</span><span class="sxs-lookup"><span data-stu-id="903d6-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="903d6-103">Türetilen bir sınıfta geçersiz kılındığında, akış tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="903d6-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="903d6-104">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="903d6-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="903d6-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="903d6-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="903d6-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="903d6-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="903d6-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="903d6-107">Parameters</span></span>

`value`\
<span data-ttu-id="903d6-108">İstenen bayt cinsinden geçerli akış uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="903d6-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="903d6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="903d6-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="903d6-110">`SqlStreamChars.SetLength` Yöntemi private olduğuna ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="903d6-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="903d6-111">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="903d6-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="903d6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="903d6-112">Requirements</span></span>

<span data-ttu-id="903d6-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="903d6-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="903d6-114">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="903d6-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="903d6-115">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="903d6-115">**.NET Framework versions:** Available since 2.0.</span></span>