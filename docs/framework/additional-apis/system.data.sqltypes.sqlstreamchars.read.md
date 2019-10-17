---
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
ms.openlocfilehash: 9c8a1526e75fdc304022e74a7cc52506762489ea
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395746"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="01bfa-102">SqlStreamChars. Read (Char [], Int32, Int32) yöntemi</span><span class="sxs-lookup"><span data-stu-id="01bfa-102">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="01bfa-103">Türetilmiş bir sınıfta geçersiz kılınırsa, giriş akışından sonraki karakter kümesini okur.</span><span class="sxs-lookup"><span data-stu-id="01bfa-103">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="01bfa-104">Bu yöntemi içeren derlemenin SQLAccess. dll ile bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="01bfa-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="01bfa-105">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="01bfa-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="01bfa-106">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="01bfa-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="01bfa-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01bfa-107">Parameters</span></span>

`buffer`\
<span data-ttu-id="01bfa-108">Okunacak bir Char dizisi.</span><span class="sxs-lookup"><span data-stu-id="01bfa-108">A char array to read.</span></span>

`offset`\
<span data-ttu-id="01bfa-109">Kaynağa göre bir göreli konum.</span><span class="sxs-lookup"><span data-stu-id="01bfa-109">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="01bfa-110">Geçerli akıştan okunacak karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="01bfa-110">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="01bfa-111">Döndürür</span><span class="sxs-lookup"><span data-stu-id="01bfa-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="01bfa-112">Arabelleğe okunan toplam karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="01bfa-112">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="01bfa-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01bfa-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="01bfa-114">@No__t-0 Yöntemi özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="01bfa-114">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="01bfa-115">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="01bfa-115">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="01bfa-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01bfa-116">Requirements</span></span>

<span data-ttu-id="01bfa-117">**Ad alanı:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="01bfa-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="01bfa-118">**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)</span><span class="sxs-lookup"><span data-stu-id="01bfa-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="01bfa-119">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01bfa-119">**.NET Framework versions:** Available since 2.0.</span></span>
