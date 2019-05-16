---
title: SqlStreamChars.Read (Char [], Int32, Int32) yöntemi (System.Data.SqlTypes)
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
ms.openlocfilehash: df715f622f874b3c9297c421eab9f4c7504e696b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634313"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="66eb4-102">SqlStreamChars.Read (Char [], Int32, Int32) yöntemi</span><span class="sxs-lookup"><span data-stu-id="66eb4-102">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="66eb4-103">Sonraki karakter kümesini, türetilen bir sınıfta geçersiz kılındığında, giriş akışından okur.</span><span class="sxs-lookup"><span data-stu-id="66eb4-103">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="66eb4-104">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="66eb4-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="66eb4-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="66eb4-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="66eb4-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="66eb4-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="66eb4-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66eb4-107">Parameters</span></span>

`buffer`\
<span data-ttu-id="66eb4-108">Okunacak karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="66eb4-108">A char array to read.</span></span>

`offset`\
<span data-ttu-id="66eb4-109">Kaynağa göre bir uzaklık.</span><span class="sxs-lookup"><span data-stu-id="66eb4-109">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="66eb4-110">Geçerli akışından okunacak karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="66eb4-110">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="66eb4-111">Döndürür</span><span class="sxs-lookup"><span data-stu-id="66eb4-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="66eb4-112">Arabelleğe okunan karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="66eb4-112">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="66eb4-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66eb4-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="66eb4-114">`SqlStreamChars.Read` Yöntemi private olduğuna ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="66eb4-114">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="66eb4-115">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="66eb4-115">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="66eb4-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66eb4-116">Requirements</span></span>

<span data-ttu-id="66eb4-117">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="66eb4-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="66eb4-118">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="66eb4-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="66eb4-119">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66eb4-119">**.NET Framework versions:** Available since 2.0.</span></span>
