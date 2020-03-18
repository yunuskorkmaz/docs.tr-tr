---
title: XAttribute Sınıf Genel Bakış (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 7a806314664c6319fc45cff0dddedbe38027059d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635671"
---
# <a name="xattribute-class-overview-c"></a>XAttribute Sınıf Genel Bakış (C#)
Öznitelikler, bir öğeyle ilişkili ad/değer çiftleridir. Sınıf <xref:System.Xml.Linq.XAttribute> XML özniteliklerini temsil eder.  
  
## <a name="overview"></a>Genel Bakış  
 Öznitelikleri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ile çalışma öğeleri ile çalışmaya benzer. Yapıcıları benzer. Bunların koleksiyonlarını almak için kullandığınız yöntemler benzerdir. Özniteliklerin bir koleksiyonu için linq sorgu ifadesi, öğeler topluluğu için linq sorgu ifadesine çok benzer görünür.  
  
 Özniteliklerin bir öğeye eklenme sırası korunur. Diğer bir deyişle, öznitelikleri doğruladığınızda, onları eklendikleri sırada görürsünüz.  
  
## <a name="the-xattribute-constructor"></a>XAttribute Oluşturucu  
 <xref:System.Xml.Linq.XAttribute> Sınıfın aşağıdaki oluşturucusu en sık kullanacağınız şeydir:  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Bir <xref:System.Xml.Linq.XAttribute> nesnesi oluşturur. Bağımsız `name` değişken öznitelik adını belirtir; `content` özniteliğin içeriğini belirtir.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Öznitelik ile Bir Öğe Oluşturma  
 Aşağıdaki kod, öznitelik içeren bir öğe oluşturma ortak görevi gösterir:  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>Niteliklerin Fonksiyonel Yapısı  
 Aşağıdaki gibi <xref:System.Xml.Linq.XAttribute> nesnelerin yapısı <xref:System.Xml.Linq.XElement> ile sıralı nesneleri oluşturabilirsiniz:  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
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
  
### <a name="attributes-are-not-nodes"></a>Öznitelikler Düğüm Değildir  
 Öznitelikler ve öğeler arasında bazı farklılıklar vardır. <xref:System.Xml.Linq.XAttribute>nesneler XML ağacında düğüm değildir. Bunlar bir XML öğesi ile ilişkili ad/değer çiftleridir. Belge Nesnesi Modeli'nin (DOM) aksine, bu xml yapısını daha yakından yansıtır. Nesneler <xref:System.Xml.Linq.XAttribute> XML ağacında fiilen düğüm ler olmasa <xref:System.Xml.Linq.XAttribute> da, nesnelerle çalışmak <xref:System.Xml.Linq.XElement> nesnelerle çalışmaya çok benzer.  
  
 Bu ayrım, öncelikle düğüm düzeyinde XML ağaçları ile çalışan kod yazan geliştiriciler için önemlidir. Birçok geliştirici bu ayrım ile ilgili olmayacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Programlamaya Genel Bakış (C#)](./linq-to-xml-overview.md)
