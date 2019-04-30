---
title: SqlStreamChars.Close yöntemi (System.Data.SqlTypes)
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
ms.openlocfilehash: d0c29bbc5c6bea98cf36e3c2b6bf7825d6843ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705876"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="30e7e-102">SqlStreamChars.Close yöntemi</span><span class="sxs-lookup"><span data-stu-id="30e7e-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="30e7e-103">Geçerli akışı kapatır ve akış ile ilişkili tüm sistem kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="30e7e-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="30e7e-104">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="30e7e-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="30e7e-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="30e7e-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="30e7e-106"> Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="30e7e-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="30e7e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30e7e-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="30e7e-108">`SqlStreamChars.Close` Yöntemi private olduğuna ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="30e7e-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="30e7e-109">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="30e7e-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="30e7e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30e7e-110">Requirements</span></span>

<span data-ttu-id="30e7e-111">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="30e7e-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="30e7e-112">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="30e7e-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="30e7e-113">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="30e7e-113">**.NET Framework versions:** Available since 2.0.</span></span>