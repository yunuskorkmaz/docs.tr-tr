---
title: XAttribute Sınıfına Genel Bakış
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: ceafe5478e41fb4c2038fd9300ef7b1ee6cb8411
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636659"
---
# <a name="xattribute-class-overview-visual-basic"></a>XAttribute sınıfına genel bakış (Visual Basic)
Öznitelikler, bir öğesiyle ilişkili ad/değer çiftleridir. <xref:System.Xml.Linq.XAttribute> sınıfı XML özniteliklerini temsil eder.  
  
## <a name="overview"></a>Genel bakış  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] özniteliklerle çalışma, öğelerle çalışmaya benzer. Oluşturucular benzerdir. Bunların koleksiyonlarını almak için kullandığınız yöntemler benzerdir. Öznitelik koleksiyonu için LINQ sorgu ifadesi bir öğe koleksiyonu için LINQ sorgu ifadesine çok benzer şekilde görünür.  
  
 Öznitelikleri bir öğeye eklenme sırası korunur. Diğer bir deyişle, özniteliklerde yineleme yaparken, bunları eklendiği sırayla görürsünüz.  
  
## <a name="the-xattribute-constructor"></a>XAttribute Oluşturucusu  
 <xref:System.Xml.Linq.XAttribute> sınıfının aşağıdaki Oluşturucusu, en sık kullandığınız bir sınıftır:  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Oluşturur bir <xref:System.Xml.Linq.XAttribute> nesne. `name` bağımsız değişkeni özniteliğin adını belirtir; `content` özniteliğin içeriğini belirtir.|  
  
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
 <xref:System.Xml.Linq.XElement> nesnelerinin yapımını aşağıdaki gibi <xref:System.Xml.Linq.XAttribute> nesneleri satır içinde oluşturabilirsiniz:  
  
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
 Öznitelikler ve öğeler arasında bazı farklılıklar vardır. <xref:System.Xml.Linq.XAttribute> nesneler XML ağacındaki düğümler değildir. Bunlar bir XML öğesiyle ilişkili ad/değer çiftleridir. Belge Nesne Modeli (DOM) aksine bu, XML yapısını daha yakından yansıtır. <xref:System.Xml.Linq.XAttribute> nesneler gerçekten XML ağacında düğümler olmasa da, <xref:System.Xml.Linq.XAttribute> nesneleriyle çalışma <xref:System.Xml.Linq.XElement> nesneleriyle çalışmaya çok benzer.  
  
 Bu ayrım, birincil olarak yalnızca düğüm düzeyindeki XML ağaçları ile çalışan kod yazan geliştiriciler için önemlidir. Birçok geliştirici bu ayrım ile ilgilenmeyecektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
