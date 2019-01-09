---
title: SqlChars.Stream özelliği (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: f8b6f4f3a92f1d78e434263c6a7897641867c412
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152202"
---
# <a name="sqlcharsstream-property"></a><span data-ttu-id="f0aeb-102">SqlChars.Stream özelliği</span><span class="sxs-lookup"><span data-stu-id="f0aeb-102">SqlChars.Stream Property</span></span>

<span data-ttu-id="f0aeb-103">Alır veya ayarlar karakter akışı.</span><span class="sxs-lookup"><span data-stu-id="f0aeb-103">Gets or sets the character stream.</span></span> <span data-ttu-id="f0aeb-104">Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="f0aeb-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="f0aeb-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="f0aeb-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="f0aeb-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0aeb-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="f0aeb-107">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="f0aeb-107">Property value</span></span>

`System.Data.SqlTypes.SqlStreamChars`\
<span data-ttu-id="f0aeb-108">Karakter akış.</span><span class="sxs-lookup"><span data-stu-id="f0aeb-108">The character stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="f0aeb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0aeb-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f0aeb-110">`SqlChars.Stream` Özelliği dahili kullanım içindir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="f0aeb-110">The `SqlChars.Stream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f0aeb-111">Microsoft hiçbir koşulda, bir üretim uygulamasında bu özelliğin kullanımı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f0aeb-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0aeb-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0aeb-112">Requirements</span></span>

<span data-ttu-id="f0aeb-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="f0aeb-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="f0aeb-114">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="f0aeb-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="f0aeb-115">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0aeb-115">**.NET Framework versions:** Available since 2.0.</span></span>