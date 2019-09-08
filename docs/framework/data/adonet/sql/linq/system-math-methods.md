---
title: System.Math Yöntemleri
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: 0b113cefa6be040924134f9d2d0cb0c9d334feef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792395"
---
# <a name="systemmath-methods"></a>System.Math Yöntemleri
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Aşağıdaki <xref:System.Math> yöntemleri desteklemez.  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a>.NET farklılıkları  
 .NET Framework, SQL Server farklı yuvarlama semantiklerine sahiptir. .NET Framework yöntemi, sonraki daha yüksek basamak yerine, 5 içinde sonlanan sayıların en yakın çift basamağına yuvarlamasını Banker yuvarlama işlemini gerçekleştirir. <xref:System.Math.Round%2A> Örneğin, 2,5 2 ' ye yuvarlanır, ancak 3,5 4 ' e yuvarlanır. (Bu teknik, büyük veri işlemlerinde daha yüksek değerlere yönelik doğru bir sapmanın önlenmesine yardımcı olur.)  
  
 SQL 'de, `ROUND` işlev her zaman 0 ' dan uzağa yuvarlanır. Bu nedenle 2,5, .NET Framework 2 ' ye yuvarlanarak 3 ' e yuvarlanır.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL `ROUND` semantiğinin üzerinden geçer ve Banker yuvarlama uygulamayı denemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri ve İşlevleri](data-types-and-functions.md)
