---
title: SqlStreamChars.SetLength(Int64) yöntemi (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c7199cbd08e62b1f0391437a0c1864cb9036fe1f
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222715"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="c1ef1-102">SqlStreamChars.SetLength(Int64) yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1ef1-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="c1ef1-103">Türetilen bir sınıfta geçersiz kılındığında, akış tarafından kullanılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="c1ef1-104">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="c1ef1-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="c1ef1-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="c1ef1-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1ef1-107">Parameters</span></span>

`value`\
<span data-ttu-id="c1ef1-108">İstenen bayt cinsinden geçerli akış uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1ef1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1ef1-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="c1ef1-110">`SqlStreamChars.SetLength` Yöntemi private olduğuna ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="c1ef1-111">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c1ef1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1ef1-112">Requirements</span></span>

<span data-ttu-id="c1ef1-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="c1ef1-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="c1ef1-114">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="c1ef1-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="c1ef1-115">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-115">**.NET Framework versions:** Available since 2.0.</span></span>