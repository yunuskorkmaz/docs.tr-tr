---
title: Parçalara ayırma öncesi XName nesneleri (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: 250b7aa8060c8196c28725fded090e2a63a0ee54
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819300"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>Parçalara ayırma öncesi XName nesneleri (LINQ to XML) (Visual Basic)
LINQ to XML performansını artırmak için bir yolu önceden küçük parçalara etmektir <xref:System.Xml.Linq.XName> nesneleri. Parçalara ayırma öncesi anlamına gelir, bir dizeye atadığınız bir <xref:System.Xml.Linq.XName> oluşturucuları kullanarak XML ağacı oluşturmadan önce nesne <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> sınıfları. Ardından, oluşturucuya bir dizeyi geçirmek yerine, kullandığınız dizesine örtük dönüştürme <xref:System.Xml.Linq.XName>, başlatılmış geçirdiğiniz <xref:System.Xml.Linq.XName> nesne.  
  
 Bu, belirli adları yinelenen büyük bir XML ağacı oluştururken performansı artırır. Bunu yapmak için bildirmek ve başlatmak <xref:System.Xml.Linq.XName> XML ağacı oluşturmak ve ardından kullanmadan önce nesneleri <xref:System.Xml.Linq.XName> öğe ve öznitelik adları için dizeleri belirtmek yerine, nesneleri. Çok sayıda öğe (veya öznitelikleri) oluşturuyorsanız bu teknik, aynı ada sahip önemli ölçüde performans kazanımı sağlayabilir.  
  
 Parçalara ayırma öncesi kendi senaryonuza kullanılması gerektiği, karar vermek için test etmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bu gösterir.  
  
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
  
 Aşağıdaki örnek, XML belgesi bir ad alanında olduğu aynı tekniği gösterir:  
  
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
  
 Aşağıdaki örnek, ne, büyük olasılıkla gerçek dünyada karşınıza çıkacak için daha benzer. Bu örnekte, öğenin içeriğini bir sorgu tarafından sağlanır:  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 Önceki örnekte, adları değil önceden parçalara ayrılmış aşağıdaki örnek, daha iyi gerçekleştirir:  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [Parçalara ayrılmış XName ve XNamespace nesneleri (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
