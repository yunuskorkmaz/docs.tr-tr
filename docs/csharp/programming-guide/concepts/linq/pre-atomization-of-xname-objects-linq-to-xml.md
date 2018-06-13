---
title: Ön Atomization XName nesnelerin (LINQ-XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 8d793dcdfd2669fa96c92be0e0e3c3ebb8f38d0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329309"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a>Ön Atomization XName nesnelerin (LINQ-XML) (C#)
LINQ-XML performansını artırmak için bir yoldur önceden küçük parçalara ayrılamıyor için <xref:System.Xml.Linq.XName> nesneleri. Ön atomization anlamına gelir dizeye atadığınız bir <xref:System.Xml.Linq.XName> , oluşturucuları kullanarak XML ağaç oluşturmadan önce nesne <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> sınıfları. Ardından, oluşturucuya bir dizeye geçiliyor yerine, kullandığınız örtük bir dönüştürme için <xref:System.Xml.Linq.XName>, başlatılmış geçirdiğiniz <xref:System.Xml.Linq.XName> nesnesi.  
  
 Belirli adları yinelenen büyük bir XML ağacı oluştururken bu performansı artırır. Bunu yapmak için bildirme ve başlatma <xref:System.Xml.Linq.XName> XML ağacını oluşturmak ve ardından kullanmaya başlamadan önce nesneleri <xref:System.Xml.Linq.XName> öğe ve öznitelik adları için dizelerini belirtme yerine nesneleri. Çok sayıda öğe (ve özniteliklerin) oluşturuyorsanız, bu teknik aynı ada sahip önemli ölçüde performans artışı sağlar.  
  
 Bunu kullanmalısınız varsa karar vermek için senaryonuzun öncesi atomization test etmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bu gösterir.  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
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
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XName Root = aw + "Root";  
XName Data = aw + "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XAttribute(XNamespace.Xmlns + "aw", aw),  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
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
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
DateTime t1 = DateTime.Now;  
XElement root = new XElement(Root,  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement(Data,  
        new XAttribute(ID, i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
 Önceki örnekte, adları değil önceden atomized aşağıdaki örnek, daha iyi gerçekleştirir:  
  
```csharp  
DateTime t1 = DateTime.Now;  
XElement root = new XElement("Root",  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement("Data",  
        new XAttribute("ID", i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)  
 [Atomized XName ve XNamespace nesneleri (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
