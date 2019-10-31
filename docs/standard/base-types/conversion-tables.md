---
title: .NET 'te tür dönüştürme tabloları
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
ms.openlocfilehash: aa1ef8397338af949bd147fd3252b2d9ecaf53ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103883"
---
# <a name="type-conversion-tables-in-net"></a>.NET 'te tür dönüştürme tabloları
Genişleyen dönüştürme, bir türün değeri eşit veya daha büyük boyutta başka bir türe dönüştürüldüğünde gerçekleşir. Bir tür değeri daha küçük boyutta olan başka bir türün değerine dönüştürüldüğünde bir daraltma dönüştürmesi oluşur. Bu konudaki tablolarda her iki tür dönüştürme için de konu gösteren davranışlar gösterilmektedir.  
  
## <a name="widening-conversions"></a>Dönüştürmeleri Genişletme  
 Aşağıdaki tabloda, bilgi kaybı olmadan gerçekleştirilebilecek genişletme dönüştürmeleri açıklanmaktadır.  
  
|Tür|, Veri kaybı olmadan dönüştürülebilir|  
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
  
 <xref:System.Single> veya <xref:System.Double> bazı genişletme dönüştürmeleri duyarlık kaybına neden olabilir. Aşağıdaki tabloda bazen bilgi kaybına neden olan genişletme dönüştürmeleri açıklanmaktadır.  
  
|Tür|Dönüştürülebilir|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Daraltma dönüştürmeleri  
 <xref:System.Single> veya <xref:System.Double> bir daraltma dönüştürmesi, bilgi kaybına neden olabilir. Hedef türü kaynağın büyüklüğünü doğru bir şekilde ifade edemez, elde edilen tür sabit `PositiveInfinity` veya `NegativeInfinity`olarak ayarlanır. `PositiveInfinity`, pozitif bir sayıyı sıfıra bölüyor ve bir <xref:System.Single> ya da <xref:System.Double> değeri `MaxValue` alanının değerini aştığında de döndürülür. `NegativeInfinity`, negatif bir sayıyı sıfıra bölüden elde edilecek ve bir <xref:System.Single> veya <xref:System.Double> değeri `MinValue` alanı değerin altına düştüğünde de döndürülür. Bir <xref:System.Double> <xref:System.Single> bir dönüştürme `PositiveInfinity` veya `NegativeInfinity`neden olabilirler.  
  
 Daraltma dönüştürmesi aynı zamanda diğer veri türleri için bilgi kaybına neden olabilir. Ancak, dönüştürülmüş bir türün değeri hedef türün `MaxValue` ve `MinValue` alanları tarafından belirtilen aralığın dışında kalırsa ve dönüştürme çalışma zamanı tarafından, hedef türü değerinin aşmayacağından emin olmak için işaretlendiğinde bir <xref:System.OverflowException> oluşturulur. `MaxValue` veya `MinValue`. <xref:System.Convert?displayProperty=nameWithType> sınıfıyla gerçekleştirilen dönüşümler her zaman bu şekilde denetlenir.  
  
 Aşağıdaki tabloda, <xref:System.Convert?displayProperty=nameWithType> veya dönüştürülen tür değeri elde edilen türün tanımlı aralığının dışındaysa bir <xref:System.OverflowException> oluşturan dönüşümler listelenmektedir.  
  
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
