---
title: .NET içinde tür dönüştürme tabloları
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
ms.openlocfilehash: f018ed182e6354bbc6e6873f0df1b35e023c9c17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650329"
---
# <a name="type-conversion-tables-in-net"></a>.NET içinde tür dönüştürme tabloları
Bir türde bir değer eşit veya daha fazla boyutunu başka bir türe dönüştürüldüğünde Genişletme dönüşümü gerçekleşir. Bir türde bir değer daha küçük bir boyut başka bir türün değerine dönüştürüldüğünde bir daraltma dönüşümü gerçekleşir. Bu başlıktaki tablolar, her iki tür dönüştürmeler tarafından sergilenen davranışları gösterir.  
  
## <a name="widening-conversions"></a>Dönüştürmeleri Genişletme  
 Aşağıdaki tabloda, bilgi kaybı olmadan gerçekleştirilebilir dönüştürmelerine açıklanmaktadır.  
  
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
  
 Bazı dönüşümlerdir <xref:System.Single> veya <xref:System.Double> duyarlık kaybına neden olabilir. Aşağıdaki tabloda, bazen bir bilgi kaybına neden dönüştürmelerine açıklanmaktadır.  
  
|Tür|Dönüştürülebilir|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Daraltma dönüşümleri  
 Bir daraltma dönüşümü için <xref:System.Single> veya <xref:System.Double> bilgi kaybına neden olabilir. Hedef türü doğru kaynak büyüklüğünü express olamaz, elde edilen türü sabitine ayarlanır `PositiveInfinity` veya `NegativeInfinity`. `PositiveInfinity` sonuçları bir pozitif sayı sıfıra bölme gelen ve ne zaman da döndürülür değerini bir <xref:System.Single> veya <xref:System.Double> değerini aşıyor `MaxValue` alan. `NegativeInfinity` negatif bir sayı sıfıra bölme gelen sonuçları ve ne zaman da döndürülür değerini bir <xref:System.Single> veya <xref:System.Double> değerin altına düşerse `MinValue` alan. Dönüştürme bir <xref:System.Double> için bir <xref:System.Single> sonuçlanabilir `PositiveInfinity` veya `NegativeInfinity`.  
  
 Bir daraltma dönüşümü ayrıca diğer veri türleri için bilgi kaybına neden olabilir. Ancak, bir <xref:System.OverflowException> harflere dönüştürülecek türün değeri hedef türün tarafından belirtilen aralık dışında kalırsa durum `MaxValue` ve `MinValue` alanları ve dönüştürme hedef değeri emin olmak için çalışma zamanı tarafından denetlenir aşmayan türü kendi `MaxValue` veya `MinValue`. İle gerçekleştirilen dönüştürmeler <xref:System.Convert?displayProperty=nameWithType> sınıfı her zaman bu şekilde denetlenir.  
  
 Throw dönüştürmeler aşağıdaki tabloda bir <xref:System.OverflowException> kullanarak <xref:System.Convert?displayProperty=nameWithType> veya harflere dönüştürülecek türün değeri sonuç türünde tanımlı aralığın dışında ise herhangi işaretli dönüştürme.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Convert?displayProperty=nameWithType>
- [.NET içinde Tür Dönüştürme](../../../docs/standard/base-types/type-conversion.md)
