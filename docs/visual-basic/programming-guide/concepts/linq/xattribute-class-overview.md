---
title: XAttribute sınıfına genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 08b8ebf31a39325c98023d4bb333f8e06bbdeb3f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406434"
---
# <a name="xattribute-class-overview-visual-basic"></a>XAttribute sınıfına genel bakış (Visual Basic)
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
 Aşağıdaki kod, Visual Basic'te XML değişmez değerlerini kullanarak bir öznitelik içeren bir öğeyi gösterir:  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>İşlev öznitelikleri yapımı  
 Oluşturulabilir <xref:System.Xml.Linq.XAttribute> nesneler satır içi oluşumu ile <xref:System.Xml.Linq.XElement> gibi nesneler:  
  
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
  
### <a name="attributes-are-not-nodes"></a>Öznitelik düğümleri olmayan  
 Öznitelikler ve öğeler arasında bazı farklar vardır. <xref:System.Xml.Linq.XAttribute> nesneler XML Ağaçtaki düğümler değildir. Bunlar bir XML öğesi ile ilişkili ad/değer çiftleridir. Belge nesne modeli (DOM) aksine bu daha yakından XML yapısını yansıtır. Ancak <xref:System.Xml.Linq.XAttribute> nesneleri gerçekten düğümleri ile çalışma XML ağacında olmayan <xref:System.Xml.Linq.XAttribute> nesneler ile çalışma için çok benzer <xref:System.Xml.Linq.XElement> nesneleri.  
  
 Bu ayrım, yalnızca XML ağaçları düğüm düzeyinde çalışan kod yazma geliştiriciler öncelikle önemlidir. Bu ayrım ile ilgili birçok geliştiricinin olmayacaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to XML programlamaya genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
