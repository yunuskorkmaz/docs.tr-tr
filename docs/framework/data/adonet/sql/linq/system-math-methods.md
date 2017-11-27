---
title: "System.Math yöntemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: af5e18b9c4334cfab26c9a84ac647bb433391ef1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="systemmath-methods"></a>System.Math yöntemleri
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Aşağıdaki desteklemiyor <xref:System.Math> yöntemleri.  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a>.NET arasındaki farklar  
 .NET Framework, SQL Server'dan farklı yuvarlama semantiği sahiptir. <xref:System.Math.Round%2A> Yöntemi .NET Framework'teki gerçekleştirir *Banker yuvarlaması*,.5 içinde sona erer numaraları yuvarlanacağını burada yerine çift basamaklı sonraki yüksek sayıya en yakın. Örneğin, 3.5 4'e yuvarlar sırada 2.5 2'ye yuvarlar. (Bu teknik daha yüksek değerleri büyük veri işlemlerde doğru sistematik sapması önlemeye yardımcı olur.)  
  
 SQL'de, `ROUND` işlevi yerine 0 çıktığınızda her zaman yuvarlar. Bu nedenle, .NET Framework 2. yuvarlama ile contrasted 3 2.5 yuvarlar.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL geçirir aracılığıyla `ROUND` semantiği ve Banker yuvarlaması uygulamak denemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri türleri ve işlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
