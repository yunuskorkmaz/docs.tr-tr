---
title: LINQ to XML dinamik özellikler başvurusu
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: ca3684716f9b562d0e6a006c26730a1d1a28f8b1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920932"
---
# <a name="linq-to-xml-dynamic-properties"></a>LINQ to XML dinamik özellikleri

Bu bölüm LINQ to XML içindeki dinamik özelliklerle ilgili başvuru bilgileri sağlar. Özellikle, bu özellikler <xref:System.Xml.Linq> ad alanındaki <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> sınıfları tarafından gösterilir.

[LINQ to XML Ile WPF veri bağlamaya genel bakış](wpf-data-binding-with-linq-to-xml-overview.md)konusunda açıklandığı gibi, dinamik özelliklerin her biri aynı sınıftaki standart ortak bir özellik veya yönteme eşdeğerdir. Bu standart Üyeler çoğu amaçla kullanılmalıdır; dinamik özellikler, LINQ to XML veri bağlama senaryoları için özel olarak sağlanır. Bu sınıfların standart üyeleri hakkında daha fazla bilgi için, <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> başvuru konularına bakın.

Çözümlenme değerlerine göre, bu bölümdeki dinamik özellikler iki kategoriye ayrılır:

- Tek bir değere çözüm veren <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> sınıflarında `Value` özellikleri gibi basit olanlar.

- Dizin Oluşturucu türünde çözümlenilen <xref:System.Xml.Linq.XElement> [öğeleri](elements-xelement-dynamic-property.md) ve [alt](descendants-xelement-dynamic-property.md) öğeler gibi dizinli değerler. Dizin Oluşturucu türlerinin istenen değere veya koleksiyona çözümlenmesi için, bir genişletilmiş ad parametresi geçirilmesi gerekir.

<xref:System.Collections.Generic.IEnumerable%601> türünde dizinli bir değer döndüren tüm dinamik özellikler ertelenmiş yürütmeyi kullanır. Ertelenmiş yürütme hakkında daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="reference"></a>Başvuru

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML ile WPF verilerini bağlama](wpf-data-binding-with-linq-to-xml-overview.md)
- [LINQ to XML genel bakış ile WPF veri bağlama](wpf-data-binding-with-linq-to-xml-overview.md)
- [LINQ Sorgularına Giriş (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
