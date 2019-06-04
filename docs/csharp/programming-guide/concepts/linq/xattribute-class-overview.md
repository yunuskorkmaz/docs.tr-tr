---
title: XAttribute sınıfına genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 0440e8271edcf54d00a56e2987235afd260f9156
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483188"
---
# <a name="xattribute-class-overview-c"></a>XAttribute sınıfına genel bakış (C#)
Öznitelikleri bir öğe ile ilişkili ad/değer çiftleridir. <xref:System.Xml.Linq.XAttribute> Sınıfı için XML özniteliklerini temsil eder.  
  
## <a name="overview"></a>Genel Bakış  
 Öznitelikleri ile çalışma [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğeleri ile çalışmaya benzer. Oluşturucuları benzerdir. Bunları koleksiyonlarını almak için kullandığınız yöntemleri benzerdir. A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] özniteliklerin bir koleksiyonu için sorgu ifadesi çok benzer görünür bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadesi öğelerinin koleksiyonu.  
  
 Öznitelikleri bir öğe için eklenen sırasını korunur. Öznitelikleri yineleme yaptığınızda, diğer bir deyişle, bunları eklendikleri sırayla görürsünüz.  
  
## <a name="the-xattribute-constructor"></a>XAttribute Oluşturucusu  
 Aşağıdaki oluşturucusuna <xref:System.Xml.Linq.XAttribute> sınıfı, en sık kullanacağınız bir:  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Oluşturur bir <xref:System.Xml.Linq.XAttribute> nesne. `name` Bağımsız değişkeni belirtir; öznitelik adı `content` öznitelik içeriğini belirtir.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Bir öznitelik bir öğe oluşturma  
 Aşağıdaki kod, bir öznitelik içeren bir öğeyi oluşturma görevinin gösterir:  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>İşlev öznitelikleri yapımı  
 Oluşturulabilir <xref:System.Xml.Linq.XAttribute> nesneler satır içi oluşumu ile <xref:System.Xml.Linq.XElement> gibi nesneler:  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
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
  
### <a name="attributes-are-not-nodes"></a>Öznitelik düğümleri olmayan  
 Öznitelikler ve öğeler arasında bazı farklar vardır. <xref:System.Xml.Linq.XAttribute> nesneler XML Ağaçtaki düğümler değildir. Bunlar bir XML öğesi ile ilişkili ad/değer çiftleridir. Belge nesne modeli (DOM) aksine bu daha yakından XML yapısını yansıtır. Ancak <xref:System.Xml.Linq.XAttribute> nesneleri gerçekten düğümleri ile çalışma XML ağacında olmayan <xref:System.Xml.Linq.XAttribute> nesneler ile çalışma için çok benzer <xref:System.Xml.Linq.XElement> nesneleri.  
  
 Bu ayrım, yalnızca XML ağaçları düğüm düzeyinde çalışan kod yazma geliştiriciler öncelikle önemlidir. Bu ayrım ile ilgili birçok geliştiricinin olmayacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md)
