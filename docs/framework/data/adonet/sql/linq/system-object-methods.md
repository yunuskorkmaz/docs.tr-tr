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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 319dc7ceae191de417bbdd33a5e234b42f3454de
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
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
