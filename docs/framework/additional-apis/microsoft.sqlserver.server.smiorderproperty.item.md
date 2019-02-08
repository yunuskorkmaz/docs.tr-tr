---
title: SmiOrderProperty.Item özelliği (Microsoft.SqlServer.Server)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: cb2f6cb956f9571f9bd2ba7f86d79c5df6e72a15
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827740"
---
# <a name="smiorderpropertyitem-property"></a><span data-ttu-id="77a08-102">SmiOrderProperty.Item özelliği</span><span class="sxs-lookup"><span data-stu-id="77a08-102">SmiOrderProperty.Item Property</span></span>

<span data-ttu-id="77a08-103">Varlık için sütun sırasını alır.</span><span class="sxs-lookup"><span data-stu-id="77a08-103">Gets the column order for the entity.</span></span> <span data-ttu-id="77a08-104">Bu özellik içeren derleme SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="77a08-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="77a08-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="77a08-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="77a08-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="77a08-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="77a08-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77a08-107">Syntax</span></span>

```csharp
internal SmiColumnOrder Item { get; }
```

## <a name="property-value"></a><span data-ttu-id="77a08-108">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="77a08-108">Property value</span></span>

<span data-ttu-id="77a08-109">Sütun sırası.</span><span class="sxs-lookup"><span data-stu-id="77a08-109">The column order.</span></span>

## <a name="remarks"></a><span data-ttu-id="77a08-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77a08-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="77a08-111">`SmiOrderProperty.Item` Özelliği dahili kullanım içindir ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="77a08-111">The `SmiOrderProperty.Item` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="77a08-112">Microsoft hiçbir koşulda, bir üretim uygulamasında bu özelliğin kullanımı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="77a08-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="77a08-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77a08-113">Requirements</span></span>

<span data-ttu-id="77a08-114">**Namespace:** <xref:Microsoft.SqlServer.Server></span><span class="sxs-lookup"><span data-stu-id="77a08-114">**Namespace:** <xref:Microsoft.SqlServer.Server></span></span>

<span data-ttu-id="77a08-115">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="77a08-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="77a08-116">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77a08-116">**.NET Framework versions:** Available since 2.0.</span></span>