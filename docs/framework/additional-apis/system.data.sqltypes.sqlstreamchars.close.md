---
title: SqlStreamChars.Close yöntemi (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 634b2262ce3262b2c5971fb995b7c988f50924ed
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826895"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="8b4f4-102">SqlStreamChars.Close yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b4f4-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="8b4f4-103">Geçerli akışı kapatır ve akış ile ilişkili tüm sistem kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="8b4f4-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="8b4f4-104">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="8b4f4-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="8b4f4-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="8b4f4-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="8b4f4-106"> Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b4f4-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="8b4f4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b4f4-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="8b4f4-108">`SqlStreamChars.Close` Yöntemi private olduğuna ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="8b4f4-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="8b4f4-109">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8b4f4-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="8b4f4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b4f4-110">Requirements</span></span>

<span data-ttu-id="8b4f4-111">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="8b4f4-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="8b4f4-112">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="8b4f4-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="8b4f4-113">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b4f4-113">**.NET Framework versions:** Available since 2.0.</span></span>