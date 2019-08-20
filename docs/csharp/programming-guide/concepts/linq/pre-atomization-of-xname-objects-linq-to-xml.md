---
title: XName nesnelerinin (LINQ to XML) (C#) ön atomonu
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 2fd754a352bd2988e52ec9c67a9915a8e587b107
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591499"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a>XName nesnelerinin (LINQ to XML) (C#) ön atomonu
LINQ to XML performansını artırmanın bir yolu, önceden ayrılamaz <xref:System.Xml.Linq.XName> nesneleri kullanmaktır. Ön cekleştirme, <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> sınıflarının oluşturucularını kullanarak xml ağacını oluşturmadan önce bir nesneye bir dize atadığınız anlamına gelir. Ardından, dizeden öğesine <xref:System.Xml.Linq.XName>örtük dönüştürmeyi kullanan oluşturucuya bir dize geçirmek yerine, başlatılan <xref:System.Xml.Linq.XName> nesneyi geçirirsiniz.  
  
 Bu, belirli adların tekrarlandığı büyük bir XML ağacı oluşturduğunuzda performansı geliştirir. Bunu yapmak için, xml ağacını oluşturmadan önce <xref:System.Xml.Linq.XName> nesneleri bildirir ve başlatır ve sonra öğe ve öznitelik adları için dizeleri <xref:System.Xml.Linq.XName> belirtmek yerine nesneleri kullanın. Aynı ada sahip çok sayıda öğe (veya öznitelik) oluşturuyorsanız bu teknik önemli performans artışı elde edebilir.  
  
 Kullanmanız gerekip gerekmediğini belirlemek için senaryolarınız ile önceden atomleştirme testi yapmanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bunu gösterir.  
  
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
  
 Aşağıdaki örnek, XML belgesinin bir ad alanında bulunduğu tekniği gösterir:  
  
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
  
 Aşağıdaki örnek, gerçek dünyada büyük olasılıkla karşılaşacağınız şekilde daha benzerdir. Bu örnekte, öğesinin içeriği bir sorgu tarafından sağlanır:  
  
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
  
 Önceki örnek, şu örnekteki adların ön cede olmadığı bir daha iyi şekilde çalışır:  
  
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

- [Atomlanmış XName ve XNamespace nesneleri (LINQ to XML) (C#)](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
