---
title: System.Object Yöntemleri
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: d2b96ca9e7bedd0e0438b47698d4b963844c92f3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155646"
---
# <a name="systemobject-methods"></a>System.Object Yöntemleri

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Aşağıdaki yöntemleri destekler <xref:System.Object> .  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Aşağıdaki <xref:System.Object> yöntemleri desteklemez.  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType> ,, ve gibi ikili türler için `BINARY` `VARBINARY` `IMAGE` `TIMESTAMP` .||  
  
## <a name="differences-from-net"></a>.NET farklılıkları  

 <xref:System.Object.ToString?displayProperty=nameWithType>Double için ÇıKıŞı `CONVERT` SQL 'de SQL (nvarchar (30), @x , 2) kullanır. SQL her zaman bu durumda 16 basamak ve bilimsel gösterim kullanır (örneğin, "0.000000000000000 e + 000" 0). Sonuç olarak, <xref:System.Object.ToString?displayProperty=nameWithType> dönüştürme .NET Framework aynı dizeyi oluşturmaz <xref:System.Convert.ToString%2A?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri ve İşlevleri](data-types-and-functions.md)
