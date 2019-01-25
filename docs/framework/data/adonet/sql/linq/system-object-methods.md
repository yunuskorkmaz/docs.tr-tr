---
title: System.Object yöntemleri
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: cae06286b77e23718facfc5be2b0ac2d27381ad3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713424"
---
# <a name="systemobject-methods"></a><span data-ttu-id="b91e6-102">System.Object yöntemleri</span><span class="sxs-lookup"><span data-stu-id="b91e6-102">System.Object Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b91e6-103">şunları desteklemektedir <xref:System.Object> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="b91e6-103">supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b91e6-104">şunları desteklemez <xref:System.Object> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="b91e6-104">does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="b91e6-105"><xref:System.Object.ToString?displayProperty=nameWithType> için ikili türleri gibi `BINARY`, `VARBINARY`, `IMAGE`, ve `TIMESTAMP`.</span><span class="sxs-lookup"><span data-stu-id="b91e6-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="b91e6-106">.NET arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="b91e6-106">Differences from .NET</span></span>  
 <span data-ttu-id="b91e6-107">Çıkışı <xref:System.Object.ToString?displayProperty=nameWithType> çift SQL kullanan `CONVERT`(NVARCHAR(30), @x, 2) SQL üzerinde.</span><span class="sxs-lookup"><span data-stu-id="b91e6-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="b91e6-108">SQL her zaman 16 basamak ve bilimsel gösterim bu durumda (örneğin, "0.000000000000000e + 000" 0) kullanır.</span><span class="sxs-lookup"><span data-stu-id="b91e6-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="b91e6-109">Sonuç olarak, <xref:System.Object.ToString?displayProperty=nameWithType> dönüştürme aynı dizeyle oluşturmuyor <xref:System.Convert.ToString%2A?displayProperty=nameWithType> .NET Framework'teki.</span><span class="sxs-lookup"><span data-stu-id="b91e6-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b91e6-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b91e6-110">See also</span></span>
- [<span data-ttu-id="b91e6-111">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b91e6-111">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
