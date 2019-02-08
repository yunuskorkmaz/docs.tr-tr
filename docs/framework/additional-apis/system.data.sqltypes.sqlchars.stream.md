---
title: SqlChars.Stream özelliği (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 36a6b3f45f0832ed651dc0a613f50e7170517497
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827688"
---
# <a name="sqlcharsstream-property"></a><span data-ttu-id="d6aed-102">SqlChars.Stream özelliği</span><span class="sxs-lookup"><span data-stu-id="d6aed-102">SqlChars.Stream Property</span></span>

<span data-ttu-id="d6aed-103">Alır veya ayarlar karakter akışı.</span><span class="sxs-lookup"><span data-stu-id="d6aed-103">Gets or sets the character stream.</span></span> <span data-ttu-id="d6aed-104">Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="d6aed-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="d6aed-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="d6aed-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="d6aed-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="d6aed-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="d6aed-107">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="d6aed-107">Property value</span></span>

`System.Data.SqlTypes.SqlStreamChars`\
<span data-ttu-id="d6aed-108">Karakter akış.</span><span class="sxs-lookup"><span data-stu-id="d6aed-108">The character stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6aed-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6aed-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d6aed-110">`SqlChars.Stream` Özelliği dahili kullanım içindir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="d6aed-110">The `SqlChars.Stream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d6aed-111">Microsoft hiçbir koşulda, bir üretim uygulamasında bu özelliğin kullanımı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d6aed-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6aed-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6aed-112">Requirements</span></span>

<span data-ttu-id="d6aed-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="d6aed-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="d6aed-114">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="d6aed-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="d6aed-115">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d6aed-115">**.NET Framework versions:** Available since 2.0.</span></span>