---
title: SqlStreamChars.IsNull özelliği (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 7bef26119e31658b8495df402bbc07341cd84cf7
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222564"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="1f673-102">SqlStreamChars.IsNull özelliği</span><span class="sxs-lookup"><span data-stu-id="1f673-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="1f673-103">Türetilen bir sınıfta geçersiz kılındığında, akış olup olmadığını belirten bir değer alır `null`.</span><span class="sxs-lookup"><span data-stu-id="1f673-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="1f673-104">Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="1f673-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="1f673-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="1f673-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="1f673-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f673-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="1f673-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f673-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="1f673-108">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="1f673-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="1f673-109">`true` Akış ise `null`; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="1f673-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f673-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f673-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="1f673-111">`SqlStreamChars.IsNull` Özelliği özeldir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="1f673-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="1f673-112">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1f673-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="1f673-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f673-113">Requirements</span></span>

<span data-ttu-id="1f673-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="1f673-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="1f673-115">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="1f673-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="1f673-116">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f673-116">**.NET Framework versions:** Available since 2.0.</span></span>