---
title: System.Object Yöntemleri
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: d1a36798ef789bbc44f581dfc631feee19e1f66b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781067"
---
# <a name="systemobject-methods"></a><span data-ttu-id="33fd4-102">System.Object Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="33fd4-102">System.Object Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="33fd4-103">Aşağıdaki <xref:System.Object> yöntemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="33fd4-103">supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="33fd4-104">Aşağıdaki <xref:System.Object> yöntemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="33fd4-104">does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="33fd4-105"><xref:System.Object.ToString?displayProperty=nameWithType>,, ve `BINARY` `IMAGE` `VARBINARY` gibiikilitürleriçin`TIMESTAMP`.</span><span class="sxs-lookup"><span data-stu-id="33fd4-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="33fd4-106">.NET farklılıkları</span><span class="sxs-lookup"><span data-stu-id="33fd4-106">Differences from .NET</span></span>  
 <span data-ttu-id="33fd4-107">Double <xref:System.Object.ToString?displayProperty=nameWithType> için çıkışı SQL 'de SQL `CONVERT`(nvarchar (30), @x, 2) kullanır.</span><span class="sxs-lookup"><span data-stu-id="33fd4-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="33fd4-108">SQL her zaman bu durumda 16 basamak ve bilimsel gösterim kullanır (örneğin, "0.000000000000000 e + 000" 0).</span><span class="sxs-lookup"><span data-stu-id="33fd4-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="33fd4-109">Sonuç olarak, <xref:System.Object.ToString?displayProperty=nameWithType> dönüştürme .NET Framework aynı <xref:System.Convert.ToString%2A?displayProperty=nameWithType> dizeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="33fd4-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33fd4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33fd4-110">See also</span></span>

- [<span data-ttu-id="33fd4-111">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="33fd4-111">Data Types and Functions</span></span>](data-types-and-functions.md)
