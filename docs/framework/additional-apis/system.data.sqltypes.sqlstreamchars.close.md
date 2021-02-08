---
description: ': SqlStreamChars. Close yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 27f2ea6e288d166f3b63979a83a1cf80eeced334
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782383"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="ca335-103">SqlStreamChars. Close yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca335-103">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="ca335-104">Geçerli akışı kapatır ve akışla ilişkili tüm sistem kaynaklarını serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="ca335-104">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="ca335-105">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="ca335-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="ca335-106">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ca335-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="ca335-107">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca335-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="ca335-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca335-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="ca335-109">`SqlStreamChars.Close`Yöntemi özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="ca335-109">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ca335-110">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ca335-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ca335-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca335-111">Requirements</span></span>

<span data-ttu-id="ca335-112">**Ad alanı:**<xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="ca335-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="ca335-113">**Bütünleştirilmiş kod:** System. Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="ca335-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="ca335-114">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ca335-114">**.NET Framework versions:** Available since 2.0.</span></span>
