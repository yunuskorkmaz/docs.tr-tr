---
title: .NET tür dönüştürme tabloları
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc2698a37dc77ccd8c58164ec5a34f21251b6dbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 Daraltma dönüştürmeye <xref:System.Single> veya <xref:System.Double> bilgi kaybına neden olabilir. Hedef türü sorununun kaynağının düzgün bir şekilde express olamaz, elde edilen türü sabite ayarlanır `PositiveInfinity` veya `NegativeInfinity`. `PositiveInfinity` sonuçları sıfıra pozitif bir sayı bölen ve ne zaman da döndürülür değerini bir <xref:System.Single> veya <xref:System.Double> değerini aşıyor `MaxValue` alan. `NegativeInfinity` sonuçları sıfıra negatif bir sayı bölen ve ne zaman da döndürülür değerini bir <xref:System.Single> veya <xref:System.Double> değerin altına düşerse `MinValue` alan. Bir dönüştürme bir <xref:System.Double> için bir <xref:System.Single> sonuçlanabilir `PositiveInfinity` veya `NegativeInfinity`.  
  
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
 [.NET içinde Tür Dönüştürme](../../../docs/standard/base-types/type-conversion.md)
