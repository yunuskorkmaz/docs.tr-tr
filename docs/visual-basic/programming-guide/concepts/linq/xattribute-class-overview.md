---
title: "XAttribute sınıfına genel bakış (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 900f047ec0db8ed1e2399345d2d4c3fba34afd5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xattribute-class-overview-visual-basic"></a>XAttribute sınıfına genel bakış (Visual Basic)
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
 Aşağıdaki kod, Visual Basic'te XML değişmez değerleri kullanarak bir öznitelik içeren bir öğeyi gösterir:  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>İşlev öznitelikleri yapımı  
 Oluşturabileceğiniz <xref:System.Xml.Linq.XAttribute> nesneleri satır içi yapımı ile <xref:System.Xml.Linq.XElement> nesneleri, aşağıdaki gibi:  
  
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
 Öznitelikler ve öğeler arasındaki bazı farklar vardır. <xref:System.Xml.Linq.XAttribute>nesneler düğüm XML ağacında değildir. Bunlar bir XML öğesi ile ilişkili ad/değer çiftleridir. Belge nesne modeli (DOM) aksine bu daha yakından XML yapısını yansıtır. Ancak <xref:System.Xml.Linq.XAttribute> nesneleri gerçekten çalışmaya XML Ağaçtaki düğümler olmayan <xref:System.Xml.Linq.XAttribute> nesneleri ile çalışmaya çok benzer <xref:System.Xml.Linq.XElement> nesneleri.  
  
 Bu ayrım, yalnızca XML ağaçlar olan düğüm düzeyinde çalışır kod yazma geliştiriciler öncelikle önemlidir. Geliştiricilerin çoğu Bu ayrım ile ilgilenen olmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML programlamaya genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
