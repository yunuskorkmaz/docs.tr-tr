---
title: System.Object Yöntemleri
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: 3a52f081f1c0c6e6c5218550009c736d0ed60514
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917669"
---
# <a name="systemobject-methods"></a>System.Object Yöntemleri
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] şunları desteklemektedir <xref:System.Object> yöntemleri.  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] şunları desteklemez <xref:System.Object> yöntemleri.  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType> için ikili türleri gibi `BINARY`, `VARBINARY`, `IMAGE`, ve `TIMESTAMP`.||  
  
## <a name="differences-from-net"></a>.NET arasındaki farklar  
 Çıkışı <xref:System.Object.ToString?displayProperty=nameWithType> çift SQL kullanan `CONVERT`(NVARCHAR(30), @x, 2) SQL üzerinde. SQL her zaman 16 basamak ve bilimsel gösterim bu durumda (örneğin, "0.000000000000000e + 000" 0) kullanır. Sonuç olarak, <xref:System.Object.ToString?displayProperty=nameWithType> dönüştürme aynı dizeyle oluşturmuyor <xref:System.Convert.ToString%2A?displayProperty=nameWithType> .NET Framework'teki.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
