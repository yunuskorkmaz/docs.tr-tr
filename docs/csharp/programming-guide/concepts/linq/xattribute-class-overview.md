---
title: XAttribute sınıfına genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: e0020a8cd8841ef9a35781b534c82db5e15c257f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xattribute-class-overview-c"></a>XAttribute sınıfına genel bakış (C#)
Öznitelikleri bir öğesiyle ilişkilendirilmiş olan ad/değer çiftleridir. <xref:System.Xml.Linq.XAttribute> Sınıfı, XML öznitelikleri temsil eder.  
  
## <a name="overview"></a>Genel Bakış  
 Öznitelikleri ile çalışma [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğeleriyle çalışma için benzer. Kendi oluşturucular benzerdir. Bunları koleksiyonlarını almak için kullandığınız yöntemleri benzerdir. A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] özniteliklerin bir koleksiyonu için sorgu ifadesi çok benzer şekilde görünen bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu öğe koleksiyonunu ifadesi.  
  
 Öznitelikleri bir öğe olarak eklenen sipariş korunur. Özniteliklerinden yinelemek, diğer bir deyişle, bunları bunlar eklenen sırayla görürsünüz.  
  
## <a name="the-xattribute-constructor"></a>XAttribute Oluşturucusu  
 Aşağıdaki oluşturucusunun <xref:System.Xml.Linq.XAttribute> en yaygın olarak kullanacağınız bir sınıftır:  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Oluşturur bir <xref:System.Xml.Linq.XAttribute> nesne. `name` Bağımsız değişkeni; özniteliğin adını belirtir `content` öznitelik içeriğini belirtir.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Bir öğesi olan bir öznitelik oluşturma  
 Aşağıdaki kod bir öznitelik içeren bir öğeyi oluşturma görevinin gösterir:  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>İşlev öznitelikleri yapımı  
 Oluşturabileceğiniz <xref:System.Xml.Linq.XAttribute> nesneleri satır içi yapımı ile <xref:System.Xml.Linq.XElement> nesneleri, aşağıdaki gibi:  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a>Öznitelikleri düğümleri olmayan  
 Öznitelikler ve öğeler arasındaki bazı farklar vardır. <xref:System.Xml.Linq.XAttribute> nesneler düğüm XML ağacında değildir. Bunlar bir XML öğesi ile ilişkili ad/değer çiftleridir. Belge nesne modeli (DOM) aksine bu daha yakından XML yapısını yansıtır. Ancak <xref:System.Xml.Linq.XAttribute> nesneleri gerçekten çalışmaya XML Ağaçtaki düğümler olmayan <xref:System.Xml.Linq.XAttribute> nesneleri ile çalışmaya çok benzer <xref:System.Xml.Linq.XElement> nesneleri.  
  
 Bu ayrım, yalnızca XML ağaçlar olan düğüm düzeyinde çalışır kod yazma geliştiriciler öncelikle önemlidir. Geliştiricilerin çoğu Bu ayrım ile ilgilenen olmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML programlamaya genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
