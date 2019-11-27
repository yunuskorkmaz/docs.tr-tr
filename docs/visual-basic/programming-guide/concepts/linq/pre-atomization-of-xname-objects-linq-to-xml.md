---
title: Parçalara Ayırma Öncesi XName Nesneleri (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: a87a37c5fe2fc29ca980c77d9c775b2b1e909cc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353111"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>XName nesnelerinin (LINQ to XML) ön atomda (Visual Basic)
LINQ to XML performansını artırmanın bir yolu, önceden ayrılamaz <xref:System.Xml.Linq.XName> nesneleri kullanmaktır. Ön cekleştirme, <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> sınıflarının oluşturucularını kullanarak XML ağacını oluşturmadan önce bir <xref:System.Xml.Linq.XName> nesnesine bir dize atamanız anlamına gelir. Sonra, dizeden <xref:System.Xml.Linq.XName>örtük dönüştürmeyi kullanan oluşturucuya bir dize geçirmek yerine, başlatılan <xref:System.Xml.Linq.XName> nesnesini geçirirsiniz.  
  
 Bu, belirli adların tekrarlandığı büyük bir XML ağacı oluşturduğunuzda performansı geliştirir. Bunu yapmak için, XML ağacını oluşturmadan önce <xref:System.Xml.Linq.XName> nesneleri bildirip başlatın ve ardından öğe ve öznitelik adları için dizeleri belirtmek yerine <xref:System.Xml.Linq.XName> nesneleri kullanın. Aynı ada sahip çok sayıda öğe (veya öznitelik) oluşturuyorsanız bu teknik önemli performans artışı elde edebilir.  
  
 Kullanmanız gerekip gerekmediğini belirlemek için senaryolarınız ile önceden atomleştirme testi yapmanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bunu gösterir.  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 Aşağıdaki örnek, XML belgesinin bir ad alanında bulunduğu tekniği gösterir:  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 Aşağıdaki örnek, gerçek dünyada büyük olasılıkla karşılaşacağınız şekilde daha benzerdir. Bu örnekte, öğesinin içeriği bir sorgu tarafından sağlanır:  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 Önceki örnek, şu örnekteki adların ön cede olmadığı bir daha iyi şekilde çalışır:  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [Atomlanmış XName ve XNamespace nesneleri (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
