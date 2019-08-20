---
title: XAttribute sınıfına genel bakışC#()
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 79ef00aa79be0c743423cfba1a911b238ff9a7ca
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590919"
---
# <a name="xattribute-class-overview-c"></a>XAttribute sınıfına genel bakışC#()
Öznitelikler, bir öğesiyle ilişkili ad/değer çiftleridir. <xref:System.Xml.Linq.XAttribute> Sınıfı XML özniteliklerini temsil eder.  
  
## <a name="overview"></a>Genel Bakış  
 İçindeki [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] özniteliklerle çalışma, öğelerle çalışmaya benzerdir. Oluşturucular benzerdir. Bunların koleksiyonlarını almak için kullandığınız yöntemler benzerdir. Öznitelik koleksiyonu için bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguifadesibiröğekoleksiyonuiçinsorguifadesineçokbenzerşekildegörünür.[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]  
  
 Öznitelikleri bir öğeye eklenme sırası korunur. Diğer bir deyişle, özniteliklerde yineleme yaparken, bunları eklendiği sırayla görürsünüz.  
  
## <a name="the-xattribute-constructor"></a>XAttribute Oluşturucusu  
 <xref:System.Xml.Linq.XAttribute> Sınıfının aşağıdaki Oluşturucusu, en yaygın olarak kullanabileceğiniz bir sınıftır:  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Oluşturur bir <xref:System.Xml.Linq.XAttribute> nesne. `name` Bağımsız değişken özniteliğin adını belirtir; `content` özniteliğin içeriğini belirtir.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Özniteliği olan bir öğe oluşturma  
 Aşağıdaki kod, bir özniteliği içeren bir öğe oluşturma ortak görevini gösterir:  
  
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
  
### <a name="functional-construction-of-attributes"></a>Özniteliklerin işlevsel olarak oluşturulması  
 Nesneleri oluşturmak <xref:System.Xml.Linq.XAttribute> için <xref:System.Xml.Linq.XElement> aşağıdaki gibi nesneleri satır içinde oluşturabilirsiniz:  
  
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
  
### <a name="attributes-are-not-nodes"></a>Öznitelikler düğüm değil  
 Öznitelikler ve öğeler arasında bazı farklılıklar vardır. <xref:System.Xml.Linq.XAttribute>nesneler XML ağacındaki düğümler değildir. Bunlar bir XML öğesiyle ilişkili ad/değer çiftleridir. Belge Nesne Modeli (DOM) aksine bu, XML yapısını daha yakından yansıtır. Nesneler <xref:System.Xml.Linq.XAttribute> gerçekte XML ağacında düğümler olmasa da nesnelerle <xref:System.Xml.Linq.XAttribute> çalışma, <xref:System.Xml.Linq.XElement> nesnelerle çalışmaya çok benzer.  
  
 Bu ayrım, birincil olarak yalnızca düğüm düzeyindeki XML ağaçları ile çalışan kod yazan geliştiriciler için önemlidir. Birçok geliştirici bu ayrım ile ilgilenmeyecektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakışC#()](./linq-to-xml-overview.md)
