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
# <a name="systemobject-methods"></a>System.Object Yöntemleri
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Aşağıdaki <xref:System.Object> yöntemleri destekler.  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Aşağıdaki <xref:System.Object> yöntemleri desteklemez.  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>,, ve `BINARY` `IMAGE` `VARBINARY` gibiikilitürleriçin`TIMESTAMP`.||  
  
## <a name="differences-from-net"></a>.NET farklılıkları  
 Double <xref:System.Object.ToString?displayProperty=nameWithType> için çıkışı SQL 'de SQL `CONVERT`(nvarchar (30), @x, 2) kullanır. SQL her zaman bu durumda 16 basamak ve bilimsel gösterim kullanır (örneğin, "0.000000000000000 e + 000" 0). Sonuç olarak, <xref:System.Object.ToString?displayProperty=nameWithType> dönüştürme .NET Framework aynı <xref:System.Convert.ToString%2A?displayProperty=nameWithType> dizeyi oluşturmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri ve İşlevleri](data-types-and-functions.md)
