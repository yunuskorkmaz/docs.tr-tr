---
description: 'Daha fazla bilgi edinin: System. Object yöntemleri'
title: System.Object Yöntemleri
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: 88ba4cf7cfc7dc9bea565b4689f77d088d424c44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681336"
---
# <a name="systemobject-methods"></a><span data-ttu-id="1485a-103">System.Object Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="1485a-103">System.Object Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="1485a-104">Aşağıdaki yöntemleri destekler <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="1485a-104">supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="1485a-105">Aşağıdaki <xref:System.Object> yöntemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1485a-105">does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="1485a-106"><xref:System.Object.ToString?displayProperty=nameWithType> ,, ve gibi ikili türler için `BINARY` `VARBINARY` `IMAGE` `TIMESTAMP` .</span><span class="sxs-lookup"><span data-stu-id="1485a-106"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="1485a-107">.NET farklılıkları</span><span class="sxs-lookup"><span data-stu-id="1485a-107">Differences from .NET</span></span>  

 <span data-ttu-id="1485a-108"><xref:System.Object.ToString?displayProperty=nameWithType>Double için ÇıKıŞı `CONVERT` SQL 'de SQL (nvarchar (30), @x , 2) kullanır.</span><span class="sxs-lookup"><span data-stu-id="1485a-108">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="1485a-109">SQL her zaman bu durumda 16 basamak ve bilimsel gösterim kullanır (örneğin, "0.000000000000000 e + 000" 0).</span><span class="sxs-lookup"><span data-stu-id="1485a-109">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="1485a-110">Sonuç olarak, <xref:System.Object.ToString?displayProperty=nameWithType> dönüştürme .NET Framework aynı dizeyi oluşturmaz <xref:System.Convert.ToString%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1485a-110">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1485a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1485a-111">See also</span></span>

- [<span data-ttu-id="1485a-112">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1485a-112">Data Types and Functions</span></span>](data-types-and-functions.md)
