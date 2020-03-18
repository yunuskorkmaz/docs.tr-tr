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
ms.openlocfilehash: aa1ef8397338af949bd147fd3252b2d9ecaf53ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73103883"
---
# <a name="type-conversion-tables-in-net"></a>.NET’te Tür Dönüştürme Tabloları
Genişletme dönüştürme, bir türün değeri eşit veya daha büyük boyutta başka bir türe dönüştürüldüğünde oluşur. Daraltma dönüştürme, bir türün değeri daha küçük boyuttaki başka bir türün değerine dönüştürüldüğünde oluşur. Bu konuyla ilgili tablolar, her iki dönüşüm türü tarafından sergilenen davranışları göstermektedir.  
  
## <a name="widening-conversions"></a>Dönüştürmeleri Genişletme  
 Aşağıdaki tabloda, bilgi kaybı olmadan gerçekleştirilebilecek genişletme dönüşümleri açıklanmaktadır.  
  
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
  
 Bazı genişletme dönüşümleri <xref:System.Single> veya <xref:System.Double> hassas bir kaybına neden olabilir. Aşağıdaki tabloda, bazen bilgi kaybına neden olan genişleyen dönüşümler açıklanmaktadır.  
  
|Tür|Dönüştürülebilir|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Dönüşümleri Daraltma  
 Daraltma dönüştürme <xref:System.Single> <xref:System.Double> veya bilgi kaybına neden olabilir. Hedef türü kaynağın büyüklüğünü düzgün bir şekilde ifade edemiyorsa, elde `PositiveInfinity` `NegativeInfinity`edilen tür sabit veya . `PositiveInfinity`pozitif bir sayının sıfıra bölünmesinden kaynaklanır ve a <xref:System.Single> <xref:System.Double> değeri veya `MaxValue` alanın değerini aştığında da döndürülür. `NegativeInfinity`negatif bir sayının sıfıra bölünmesinden kaynaklanır ve a <xref:System.Single> <xref:System.Double> değeri veya `MinValue` alanın değerinin altına düştüğünde de döndürülür. A'dan <xref:System.Double> <xref:System.Single> a'ya `PositiveInfinity` dönüşüm, `NegativeInfinity`  
  
 Daraltma dönüştürme, diğer veri türleri için bilgi kaybına da neden olabilir. <xref:System.OverflowException> Ancak, dönüştürülen bir türün değeri hedef türün `MaxValue` ve `MinValue` alanların belirttiği aralığın dışına düşerse ve dönüşüm, hedef türün değerinin kendi `MaxValue` veya . `MinValue` <xref:System.Convert?displayProperty=nameWithType> Sınıfla gerçekleştirilen dönüşümler her zaman bu şekilde denetlenir.  
  
 Aşağıdaki tablo, dönüştürülen türün değeri elde edilen türün tanımlı aralığının <xref:System.OverflowException> dışındaysa, bir kullanımı <xref:System.Convert?displayProperty=nameWithType> veya denetlenen dönüşüm leri içeren dönüşümleri listeler.  
  
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
