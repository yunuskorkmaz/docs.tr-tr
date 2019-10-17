---
title: SqlStreamChars. length Özelliği (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 2171b10d1c0eb7bcad894cc44c5103bdab18b0a5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395601"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="e7db2-102">SqlStreamChars. length özelliği</span><span class="sxs-lookup"><span data-stu-id="e7db2-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="e7db2-103">Türetilmiş bir sınıfta geçersiz kılındığında, geçerli akışın uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="e7db2-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="e7db2-104">Bu özelliği içeren derlemenin SQLAccess. dll ile bir Friend ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="e7db2-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e7db2-105">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e7db2-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e7db2-106">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7db2-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="e7db2-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7db2-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="e7db2-108">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="e7db2-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="e7db2-109">Akışın uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="e7db2-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7db2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7db2-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e7db2-111">@No__t-0 özelliği özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7db2-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e7db2-112">Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e7db2-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7db2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7db2-113">Requirements</span></span>

<span data-ttu-id="e7db2-114">**Ad alanı:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e7db2-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e7db2-115">**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)</span><span class="sxs-lookup"><span data-stu-id="e7db2-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e7db2-116">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e7db2-116">**.NET Framework versions:** Available since 2.0.</span></span>
