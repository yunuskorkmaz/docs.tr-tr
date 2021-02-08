---
description: ': SqlChars. Stream özelliği hakkında daha fazla bilgi'
title: SqlChars. Stream özelliği (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
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
ms.openlocfilehash: 9af0df98b268a749d890ab1b40dddbbe98ced8d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802651"
---
# <a name="sqlcharsstream-property"></a><span data-ttu-id="1bd8e-103">SqlChars.Stream Özelliği</span><span class="sxs-lookup"><span data-stu-id="1bd8e-103">SqlChars.Stream Property</span></span>

<span data-ttu-id="1bd8e-104">Karakter akışını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1bd8e-104">Gets or sets the character stream.</span></span> <span data-ttu-id="1bd8e-105">Bu özelliği içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="1bd8e-105">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="1bd8e-106">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1bd8e-106">It's intended for use by SQL Server.</span></span> <span data-ttu-id="1bd8e-107">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="1bd8e-107">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="1bd8e-108">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="1bd8e-108">Property value</span></span>

`System.Data.SqlTypes.SqlStreamChars`\
<span data-ttu-id="1bd8e-109">Karakter akışı.</span><span class="sxs-lookup"><span data-stu-id="1bd8e-109">The character stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="1bd8e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bd8e-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="1bd8e-111">`SqlChars.Stream`Özelliği Dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1bd8e-111">The `SqlChars.Stream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="1bd8e-112">Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1bd8e-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="1bd8e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1bd8e-113">Requirements</span></span>

<span data-ttu-id="1bd8e-114">**Ad alanı:**<xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="1bd8e-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="1bd8e-115">**Bütünleştirilmiş kod:** System. Data (System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="1bd8e-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="1bd8e-116">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1bd8e-116">**.NET Framework versions:** Available since 2.0.</span></span>
