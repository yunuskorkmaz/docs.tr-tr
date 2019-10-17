---
title: SqlStreamChars. Close yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c33c60842d181be7011528ca7550f3d09f291f43
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395632"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="2df83-102">SqlStreamChars. Close yöntemi</span><span class="sxs-lookup"><span data-stu-id="2df83-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="2df83-103">Geçerli akışı kapatır ve akışla ilişkili tüm sistem kaynaklarını serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="2df83-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="2df83-104">Bu yöntemi içeren derlemenin SQLAccess. dll ile bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="2df83-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="2df83-105">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2df83-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="2df83-106"> Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="2df83-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="2df83-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2df83-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="2df83-108">@No__t-0 Yöntemi özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2df83-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="2df83-109">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2df83-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="2df83-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2df83-110">Requirements</span></span>

<span data-ttu-id="2df83-111">**Ad alanı:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="2df83-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="2df83-112">**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)</span><span class="sxs-lookup"><span data-stu-id="2df83-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="2df83-113">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2df83-113">**.NET Framework versions:** Available since 2.0.</span></span>
