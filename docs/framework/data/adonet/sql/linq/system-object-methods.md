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
ms.workload: dotnet
ms.openlocfilehash: 98a1d690dbd059574098b044dd1d94b1f8792e75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemobject-methods"></a>System.Object yöntemleri
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Aşağıdaki destekleyen <xref:System.Object> yöntemleri.  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Aşağıdaki desteklemiyor <xref:System.Object> yöntemleri.  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>için ikili türleri gibi `BINARY`, `VARBINARY`, `IMAGE`, ve `TIMESTAMP`.||  
  
## <a name="differences-from-net"></a>.NET arasındaki farklar  
 Çıktısını <xref:System.Object.ToString?displayProperty=nameWithType> çift SQL kullanan `CONVERT`(NVARCHAR(30), @x, 2) SQL üzerinde. SQL her zaman 16 basamak ve bilimsel gösterim bu durumda (örneğin, "0.000000000000000e + 000" 0) kullanır. Sonuç olarak, <xref:System.Object.ToString?displayProperty=nameWithType> dönüştürme aynı dize olarak üretmek değil <xref:System.Convert.ToString%2A?displayProperty=nameWithType> .NET Framework'teki.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
