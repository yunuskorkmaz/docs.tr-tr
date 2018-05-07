---
title: Ön Atomization XName nesnelerin (LINQ-XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: 141aa5e19e75e4a09b2d7aa04d83e8a24d2a27f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>Ön Atomization XName nesnelerin (LINQ-XML) (Visual Basic)
LINQ-XML performansını artırmak için bir yoldur önceden küçük parçalara ayrılamıyor için <xref:System.Xml.Linq.XName> nesneleri. Ön atomization anlamına gelir dizeye atadığınız bir <xref:System.Xml.Linq.XName> , oluşturucuları kullanarak XML ağaç oluşturmadan önce nesne <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> sınıfları. Ardından, oluşturucuya bir dizeye geçiliyor yerine, kullandığınız örtük bir dönüştürme için <xref:System.Xml.Linq.XName>, başlatılmış geçirdiğiniz <xref:System.Xml.Linq.XName> nesnesi.  
  
 Belirli adları yinelenen büyük bir XML ağacı oluştururken bu performansı artırır. Bunu yapmak için bildirme ve başlatma <xref:System.Xml.Linq.XName> XML ağacını oluşturmak ve ardından kullanmaya başlamadan önce nesneleri <xref:System.Xml.Linq.XName> öğe ve öznitelik adları için dizelerini belirtme yerine nesneleri. Çok sayıda öğe (ve özniteliklerin) oluşturuyorsanız, bu teknik aynı ada sahip önemli ölçüde performans artışı sağlar.  
  
 Bunu kullanmalısınız varsa karar vermek için senaryonuzun öncesi atomization test etmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bu gösterir.  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 Aşağıdaki örnek, XML belgesi bir ad alanındaki olduğu aynı tekniği gösterir:  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 Aşağıdaki örnek, ne, büyük olasılıkla gerçek dünyada karşınıza çıkacak için daha benzer. Bu örnekte, öğenin içeriğinin bir sorgu tarafından sağlanır:  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 Önceki örnekte, adları değil önceden atomized aşağıdaki örnek, daha iyi gerçekleştirir:  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)  
 [Atomized XName ve XNamespace nesneleri (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
