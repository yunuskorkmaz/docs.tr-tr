---
title: XAttribute Sınıfına Genel Bakış
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 5b165044b4bea83e1a0789e3dd00367ed27b43e8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413212"
---
# <a name="xattribute-class-overview-visual-basic"></a>XAttribute sınıfına genel bakış (Visual Basic)
Öznitelikler, bir öğesiyle ilişkili ad/değer çiftleridir. <xref:System.Xml.Linq.XAttribute>Sınıfı XML özniteliklerini temsil eder.  
  
## <a name="overview"></a>Genel Bakış  
 İçindeki özniteliklerle çalışma [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , öğelerle çalışmaya benzerdir. Oluşturucular benzerdir. Bunların koleksiyonlarını almak için kullandığınız yöntemler benzerdir. Öznitelik koleksiyonu için LINQ sorgu ifadesi bir öğe koleksiyonu için LINQ sorgu ifadesine çok benzer şekilde görünür.  
  
 Öznitelikleri bir öğeye eklenme sırası korunur. Diğer bir deyişle, özniteliklerde yineleme yaparken, bunları eklendiği sırayla görürsünüz.  
  
## <a name="the-xattribute-constructor"></a>XAttribute Oluşturucusu  
 Sınıfının aşağıdaki Oluşturucusu, <xref:System.Xml.Linq.XAttribute> en yaygın olarak kullanabileceğiniz bir sınıftır:  
  
|Oluşturucu|Description|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Bir <xref:System.Xml.Linq.XAttribute> nesnesi oluşturur. `name`Bağımsız değişkeni özniteliğin adını belirtir; `content` özniteliğin içeriğini belirtir.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Özniteliği olan bir öğe oluşturma  
 Aşağıdaki kod, Visual Basic XML sabit değerlerini kullanan bir özniteliği içeren bir öğe gösterir:  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>Özniteliklerin işlevsel olarak oluşturulması  
 Nesneleri oluşturmak <xref:System.Xml.Linq.XAttribute> için aşağıdaki gibi nesneleri satır içinde oluşturabilirsiniz <xref:System.Xml.Linq.XElement> :  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
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
 Öznitelikler ve öğeler arasında bazı farklılıklar vardır. <xref:System.Xml.Linq.XAttribute>nesneler XML ağacındaki düğümler değildir. Bunlar bir XML öğesiyle ilişkili ad/değer çiftleridir. Belge Nesne Modeli (DOM) aksine bu, XML yapısını daha yakından yansıtır. <xref:System.Xml.Linq.XAttribute>Nesneler gerçekte XML ağacında düğümler olmasa da nesnelerle çalışma, <xref:System.Xml.Linq.XAttribute> nesnelerle çalışmaya çok benzer <xref:System.Xml.Linq.XElement> .  
  
 Bu ayrım, birincil olarak yalnızca düğüm düzeyindeki XML ağaçları ile çalışan kod yazan geliştiriciler için önemlidir. Birçok geliştirici bu ayrım ile ilgilenmeyecektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış (Visual Basic)](linq-to-xml-programming-overview.md)
