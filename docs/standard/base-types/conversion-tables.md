---
title: .NET’te Tür Dönüştürme Tabloları
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
ms.openlocfilehash: bb696c65078a5dae0b81a48bffc786d2257496c3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290571"
---
# <a name="type-conversion-tables-in-net"></a>.NET’te Tür Dönüştürme Tabloları
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
  
 Veya için bazı genişletme <xref:System.Single> dönüştürmeleri <xref:System.Double> duyarlık kaybına neden olabilir. Aşağıdaki tabloda bazen bilgi kaybına neden olan genişletme dönüştürmeleri açıklanmaktadır.  
  
|Tür|Dönüştürülebilir|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Daraltma dönüştürmeleri  
 Veya arasında bir daraltma <xref:System.Single> dönüştürmesi <xref:System.Double> , bilgi kaybına neden olabilir. Hedef türü kaynağın boyutunu doğru bir şekilde ifade edemez, elde edilen tür sabit veya olarak ayarlanır `PositiveInfinity` `NegativeInfinity` . `PositiveInfinity`pozitif bir sayıyı sıfıra bölen sonuçlar ve bir <xref:System.Single> veya değeri <xref:System.Double> alanın değerini aştığında de döndürülür `MaxValue` . `NegativeInfinity`negatif sayının sıfıra bölünmesiyle elde edilen sonuçlar, bir <xref:System.Single> veya değeri <xref:System.Double> alanın değerinin altına düştüğünde da döndürülür `MinValue` . ' Dan ' a dönüştürme <xref:System.Double> <xref:System.Single> , veya ile sonuçlanabilir `PositiveInfinity` `NegativeInfinity` .  
  
 Daraltma dönüştürmesi aynı zamanda diğer veri türleri için bilgi kaybına neden olabilir. Ancak, <xref:System.OverflowException> dönüştürülmekte olan bir türün değeri hedef türü ve alanları tarafından belirtilen aralığın dışında kalırsa `MaxValue` `MinValue` ve dönüştürme çalışma zamanı tarafından, hedef türü değerinin veya değerini aşmadığından emin olmak için kontrol edildiğinde oluşturulur `MaxValue` `MinValue` . Sınıfıyla gerçekleştirilen dönüşümler <xref:System.Convert?displayProperty=nameWithType> her zaman bu şekilde denetlenir.  
  
 Aşağıdaki tabloda, <xref:System.OverflowException> <xref:System.Convert?displayProperty=nameWithType> dönüştürülmüş tür değeri elde edilen türün tanımlı aralığının dışındaysa, bir using veya Checked dönüştürme oluşturan dönüşümler listelenmiştir.  
  
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
- [.NET 'te tür dönüştürme](type-conversion.md)
