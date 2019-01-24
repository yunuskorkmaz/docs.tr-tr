---
title: Parçalara ayırma öncesi XName nesneleri (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 0ea45dbf0492491efac3560b7f1f04d36a787193
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660547"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a>Parçalara ayırma öncesi XName nesneleri (LINQ to XML) (C#)
LINQ to XML performansını artırmak için bir yolu önceden küçük parçalara etmektir <xref:System.Xml.Linq.XName> nesneleri. Parçalara ayırma öncesi anlamına gelir, bir dizeye atadığınız bir <xref:System.Xml.Linq.XName> oluşturucuları kullanarak XML ağacı oluşturmadan önce nesne <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> sınıfları. Ardından, oluşturucuya bir dizeyi geçirmek yerine, kullandığınız dizesine örtük dönüştürme <xref:System.Xml.Linq.XName>, başlatılmış geçirdiğiniz <xref:System.Xml.Linq.XName> nesne.  
  
 Bu, belirli adları yinelenen büyük bir XML ağacı oluştururken performansı artırır. Bunu yapmak için bildirmek ve başlatmak <xref:System.Xml.Linq.XName> XML ağacı oluşturmak ve ardından kullanmadan önce nesneleri <xref:System.Xml.Linq.XName> öğe ve öznitelik adları için dizeleri belirtmek yerine, nesneleri. Çok sayıda öğe (veya öznitelikleri) oluşturuyorsanız bu teknik, aynı ada sahip önemli ölçüde performans kazanımı sağlayabilir.  
  
 Parçalara ayırma öncesi kendi senaryonuza kullanılması gerektiği, karar vermek için test etmeniz gerekir.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 Aşağıdaki örnek, XML belgesi bir ad alanında olduğu aynı tekniği gösterir:  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 Aşağıdaki örnek, ne, büyük olasılıkla gerçek dünyada karşınıza çıkacak için daha benzer. Bu örnekte, öğenin içeriğini bir sorgu tarafından sağlanır:  
  
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
  
 Önceki örnekte, adları değil önceden parçalara ayrılmış aşağıdaki örnek, daha iyi gerçekleştirir:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [Parçalara ayrılmış XName ve XNamespace nesneleri (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
