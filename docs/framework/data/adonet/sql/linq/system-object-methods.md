---
title: "System.Object yöntemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6998c2b00a2b8e83bc79ae7ba1dd01ea549cf5df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="systemobject-methods"></a><span data-ttu-id="2b6a7-102">System.Object yöntemleri</span><span class="sxs-lookup"><span data-stu-id="2b6a7-102">System.Object Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="2b6a7-103">Aşağıdaki destekleyen <xref:System.Object> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="2b6a7-103"> supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="2b6a7-104">Aşağıdaki desteklemiyor <xref:System.Object> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="2b6a7-104"> does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="2b6a7-105"><xref:System.Object.ToString?displayProperty=nameWithType>için ikili türleri gibi `BINARY`, `VARBINARY`, `IMAGE`, ve `TIMESTAMP`.</span><span class="sxs-lookup"><span data-stu-id="2b6a7-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="2b6a7-106">.NET arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="2b6a7-106">Differences from .NET</span></span>  
 <span data-ttu-id="2b6a7-107">Çıktısını <xref:System.Object.ToString?displayProperty=nameWithType> çift SQL kullanan `CONVERT`(NVARCHAR(30), @x, 2) SQL üzerinde.</span><span class="sxs-lookup"><span data-stu-id="2b6a7-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="2b6a7-108">SQL her zaman 16 basamak ve bilimsel gösterim bu durumda (örneğin, "0.000000000000000e + 000" 0) kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b6a7-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="2b6a7-109">Sonuç olarak, <xref:System.Object.ToString?displayProperty=nameWithType> dönüştürme aynı dize olarak üretmek değil <xref:System.Convert.ToString%2A?displayProperty=nameWithType> .NET Framework'teki.</span><span class="sxs-lookup"><span data-stu-id="2b6a7-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b6a7-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b6a7-110">See Also</span></span>  
 [<span data-ttu-id="2b6a7-111">Veri türleri ve işlevleri</span><span class="sxs-lookup"><span data-stu-id="2b6a7-111">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
