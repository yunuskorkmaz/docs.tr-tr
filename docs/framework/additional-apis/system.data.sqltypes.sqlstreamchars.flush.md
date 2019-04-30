---
title: SqlStreamChars.Flush yöntemi (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 8cd24a5ca420552f283da61ecd4edcad02965403
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705863"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="45708-102">SqlStreamChars.Flush yöntemi</span><span class="sxs-lookup"><span data-stu-id="45708-102">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="45708-103">Türetilen bir sınıfta geçersiz kılındığında, bu akış için tüm arabellekler temizler ve herhangi arabelleğe alınan verileri temel alınan cihaza yazılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="45708-103">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="45708-104">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="45708-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="45708-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="45708-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="45708-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="45708-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="45708-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45708-107">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="45708-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45708-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="45708-109">`SqlStreamChars.Flush` Yöntemi private olduğuna ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="45708-109">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="45708-110">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="45708-110">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="45708-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45708-111">Requirements</span></span>

<span data-ttu-id="45708-112">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="45708-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="45708-113">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="45708-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="45708-114">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45708-114">**.NET Framework versions:** Available since 2.0.</span></span>