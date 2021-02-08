---
description: ': SqlStreamChars. Write (Char [], Int32, Int32) yöntemi hakkında daha fazla bilgi edinin'
title: SqlStreamChars. Write (Char [], Int32, Int32) yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 3031b57902215df01c5c30625281a99be73ba2d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802560"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="da271-103">SqlStreamChars. Write (Char [], Int32, Int32) yöntemi</span><span class="sxs-lookup"><span data-stu-id="da271-103">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="da271-104">Türetilmiş bir sınıfta geçersiz kılınırsa, geçerli akışa bir karakter dizisi yazar ve yazılan karakter sayısına göre bu akış içindeki geçerli konumu ilerletir.</span><span class="sxs-lookup"><span data-stu-id="da271-104">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="da271-105">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="da271-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="da271-106">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="da271-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="da271-107">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="da271-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="da271-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="da271-108">Parameters</span></span>

`buffer`  
<span data-ttu-id="da271-109">Yazılacak bir Char dizisi.</span><span class="sxs-lookup"><span data-stu-id="da271-109">A char array to write.</span></span>

`offset`  
<span data-ttu-id="da271-110">Kaynağa göre bir göreli konum.</span><span class="sxs-lookup"><span data-stu-id="da271-110">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="da271-111">Geçerli akışa yazılacak karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="da271-111">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="da271-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da271-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="da271-113">`SqlStreamChars.Write`Yöntemi özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="da271-113">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="da271-114">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında yazma kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="da271-114">Microsoft does not support the use of this method write in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="da271-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da271-115">Requirements</span></span>

<span data-ttu-id="da271-116">**Ad alanı:**<xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="da271-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="da271-117">**Bütünleştirilmiş kod:** System. Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="da271-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="da271-118">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="da271-118">**.NET Framework versions:** Available since 2.0.</span></span>
