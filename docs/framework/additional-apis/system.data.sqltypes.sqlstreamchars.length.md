---
title: SqlStreamChars.Length özelliği (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 1ee15641e697a9d5d146f921640c73ff84a5c335
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152235"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="86381-102">SqlStreamChars.Length özelliği</span><span class="sxs-lookup"><span data-stu-id="86381-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="86381-103">Türetilen bir sınıfta geçersiz kılındığında, geçerli akış uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="86381-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="86381-104">Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="86381-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="86381-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="86381-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="86381-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="86381-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="86381-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86381-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="86381-108">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="86381-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="86381-109">Akışın uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="86381-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="86381-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86381-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="86381-111">`SqlStreamChars.Length` Özelliği özeldir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="86381-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="86381-112">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="86381-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="86381-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86381-113">Requirements</span></span>

<span data-ttu-id="86381-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="86381-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="86381-115">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="86381-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="86381-116">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="86381-116">**.NET Framework versions:** Available since 2.0.</span></span>