---
title: ".NET tür dönüştürme tabloları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET Framework], type conversions
- data types [.NET Framework], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 327469f9a151b6ef7e1c42f6669c0a9dae7016fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-conversion-tables-in-net"></a>.NET tür dönüştürme tabloları
Bir türde bir değer eşit veya daha büyük boyutta başka bir türüne dönüştürülürken dönüştürme genişletme oluşur. Bir türde bir değer daha küçük bir boyuta sahiptir başka bir türdeki bir değere dönüştürüldüğünde daraltma dönüşümü gerçekleşir. Bu konuda tablolarda her iki tür dönüşümleri tarafından sergilenen davranışları gösterilmektedir.  
  
## <a name="widening-conversions"></a>Dönüştürmeleri Genişletme  
 Aşağıdaki tabloda bilgi kaybı olmadan gerçekleştirilebilir genişletme dönüşümleri açıklanmaktadır.  
  
|Tür|Veri kaybı olmadan dönüştürülebilir|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.SByte>|<xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int16>|<xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt16>|<xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Char>|<xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int32>|<xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt32>|<xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 Bazı dönüşümleri <xref:System.Single> veya <xref:System.Double> duyarlık kaybına neden olabilir. Aşağıdaki tabloda, bazen bilgi kaybına neden genişletme dönüşümleri açıklanmaktadır.  
  
|Tür|Dönüştürülebilir|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Daraltma dönüşümleri  
 Daraltma dönüştürmeye <xref:System.Single> veya <xref:System.Double> bilgi kaybına neden olabilir. Hedef türü sorununun kaynağının düzgün bir şekilde express olamaz, elde edilen türü sabite ayarlanır `PositiveInfinity` veya `NegativeInfinity`. `PositiveInfinity`sonuçları sıfıra pozitif bir sayı bölen ve ne zaman da döndürülür değerini bir <xref:System.Single> veya <xref:System.Double> değerini aşıyor `MaxValue` alan. `NegativeInfinity`sonuçları sıfıra negatif bir sayı bölen ve ne zaman da döndürülür değerini bir <xref:System.Single> veya <xref:System.Double> değerin altına düşerse `MinValue` alan. Bir dönüştürme bir <xref:System.Double> için bir <xref:System.Single> sonuçlanabilir `PositiveInfinity` veya `NegativeInfinity`.  
  
 Daraltma dönüşümü ayrıca diğer veri türleri için bilgi kaybına neden olabilir. Ancak, bir <xref:System.OverflowException> dönüştürülecek bir türü değeri hedef tür tarafından belirtilen aralığın dışında kalırsa durum `MaxValue` ve `MinValue` alanları ve dönüştürme hedef değerini emin olmak için çalışma zamanı tarafından denetlenir aşmayan türü kendi `MaxValue` veya `MinValue`. İle gerçekleştirilen dönüşümleri <xref:System.Convert?displayProperty=nameWithType> sınıfı bu şekilde her zaman denetlenir.  
  
 Throw dönüşümleri aşağıdaki tabloda bir <xref:System.OverflowException> kullanarak <xref:System.Convert?displayProperty=nameWithType> veya dönüştürülecek türü değeri elde edilen türü tanımlı aralığın dışında ise herhangi bir dönüştürme denetledi.  
  
|Tür|Dönüştürülebilir|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Convert?displayProperty=nameWithType>  
 [.NET tür dönüştürme](../../../docs/standard/base-types/type-conversion.md)
