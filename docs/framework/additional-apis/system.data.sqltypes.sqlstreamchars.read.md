---
description: ': SqlStreamChars. Read (Char [], Int32, Int32) yöntemi hakkında daha fazla bilgi edinin'
title: SqlStreamChars. Read (Char [], Int32, Int32) yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: a899ddff7b7242fcc32aaf7b7f7794970596027b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802586"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="31b86-103">SqlStreamChars. Read (Char [], Int32, Int32) yöntemi</span><span class="sxs-lookup"><span data-stu-id="31b86-103">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="31b86-104">Türetilmiş bir sınıfta geçersiz kılınırsa, giriş akışından sonraki karakter kümesini okur.</span><span class="sxs-lookup"><span data-stu-id="31b86-104">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="31b86-105">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="31b86-105">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="31b86-106">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="31b86-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="31b86-107">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="31b86-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="31b86-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31b86-108">Parameters</span></span>

`buffer`\
<span data-ttu-id="31b86-109">Okunacak bir Char dizisi.</span><span class="sxs-lookup"><span data-stu-id="31b86-109">A char array to read.</span></span>

`offset`\
<span data-ttu-id="31b86-110">Kaynağa göre bir göreli konum.</span><span class="sxs-lookup"><span data-stu-id="31b86-110">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="31b86-111">Geçerli akıştan okunacak karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="31b86-111">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="31b86-112">Döndürülenler</span><span class="sxs-lookup"><span data-stu-id="31b86-112">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="31b86-113">Arabelleğe okunan toplam karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="31b86-113">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="31b86-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31b86-114">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="31b86-115">`SqlStreamChars.Read`Yöntemi özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="31b86-115">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="31b86-116">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="31b86-116">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="31b86-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31b86-117">Requirements</span></span>

<span data-ttu-id="31b86-118">**Ad alanı:**<xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="31b86-118">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="31b86-119">**Bütünleştirilmiş kod:** System. Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="31b86-119">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="31b86-120">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31b86-120">**.NET Framework versions:** Available since 2.0.</span></span>
