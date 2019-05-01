---
title: System.Math Yöntemleri
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: 1dae31b30962505c07c198f3bd35fceb8f400efb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917689"
---
# <a name="systemmath-methods"></a>System.Math Yöntemleri
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] şunları desteklemez <xref:System.Math> yöntemleri.  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a>.NET arasındaki farklar  
 .NET Framework, SQL Server'dan farklı yuvarlama semantiğe sahip. <xref:System.Math.Round%2A> .NET Framework'teki yöntemi gerçekleştirir *Banker yuvarlama*,.5 içinde biten sayı YUVARLA burada sonraki daha yüksek sayıya bile basamak yerine en yakın. Örneğin, 3.5, 4'e yuvarlanır sırada 2.5 2'ye yuvarlar. (Bu teknikleri sistematik sapması büyük veri işlemlerde yüksek değerler doğru önlemeye yardımcı olur.)  
  
 SQL, `ROUND` işlevi yerine 0 uzağa her zaman yuvarlar. Bu nedenle, 3, 2 .NET Framework'teki yuvarlama ile karşıtlıklar, 2.5 yuvarlar.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL geçirir aracılığıyla `ROUND` semantiği ve Banker yuvarlaması uygulamak denemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
