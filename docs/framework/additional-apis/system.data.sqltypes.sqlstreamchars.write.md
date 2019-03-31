---
title: SqlStreamChars.Write (Char [], Int32, Int32) yöntemi (System.Data.SqlTypes)
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
ms.openlocfilehash: 4084c7161eaa91d78eab32f1c14624e0032cdfcf
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675763"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="62140-102">SqlStreamChars.Write (Char [], Int32, Int32) yöntemi</span><span class="sxs-lookup"><span data-stu-id="62140-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="62140-103">Türetilen bir sınıfta geçersiz kılındığında, geçerli akışa bir karakter dizisi yazar ve geçerli konumu bu akışın içinde yazılan karakter sayısına göre ilerletir.</span><span class="sxs-lookup"><span data-stu-id="62140-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="62140-104">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="62140-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="62140-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="62140-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="62140-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="62140-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="62140-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62140-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="62140-108">Yazılacak karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="62140-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="62140-109">Kaynağa göre bir uzaklık.</span><span class="sxs-lookup"><span data-stu-id="62140-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="62140-110">Geçerli akışa yazılacak karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="62140-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="62140-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62140-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="62140-112">`SqlStreamChars.Write` Yöntemi private olduğuna ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="62140-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="62140-113">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="62140-113">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="62140-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62140-114">Requirements</span></span>

<span data-ttu-id="62140-115">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="62140-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="62140-116">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="62140-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="62140-117">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="62140-117">**.NET Framework versions:** Available since 2.0.</span></span>
