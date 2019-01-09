---
title: SqlStreamChars.Flush yöntemi (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ecaf7932a4e832a88b883ceac4746afe6140b38e
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152244"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="d1f4a-102">SqlStreamChars.Flush yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1f4a-102">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="d1f4a-103">Türetilen bir sınıfta geçersiz kılındığında, bu akış için tüm arabellekler temizler ve herhangi arabelleğe alınan verileri temel alınan cihaza yazılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="d1f4a-103">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="d1f4a-104">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="d1f4a-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="d1f4a-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="d1f4a-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="d1f4a-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1f4a-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="d1f4a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1f4a-107">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="d1f4a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1f4a-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d1f4a-109">`SqlStreamChars.Flush` Yöntemi private olduğuna ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="d1f4a-109">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d1f4a-110">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d1f4a-110">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d1f4a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1f4a-111">Requirements</span></span>

<span data-ttu-id="d1f4a-112">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="d1f4a-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="d1f4a-113">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="d1f4a-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="d1f4a-114">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1f4a-114">**.NET Framework versions:** Available since 2.0.</span></span>