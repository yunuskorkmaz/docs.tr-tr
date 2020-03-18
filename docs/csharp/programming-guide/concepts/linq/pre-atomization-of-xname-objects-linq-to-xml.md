---
title: XName Nesnelerinin Ön Atomizasyonu (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 2fd754a352bd2988e52ec9c67a9915a8e587b107
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591499"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a>XName Nesnelerinin Ön Atomizasyonu (LINQ - XML) (C#)
LINQ'daki performansı XML'e yükseltmenin bir yolu <xref:System.Xml.Linq.XName> nesneleri önceden atomize etmektir. Ön atomize, <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> xml ağacını oluşturmadan önce bir nesneye bir dize atadığınız anlamına gelir. Daha sonra, dizeden örtülü dönüştürmeyi string'e <xref:System.Xml.Linq.XName>doğru kullanan bir dizeyi <xref:System.Xml.Linq.XName> oluşturucuya geçirmek yerine, başharfe çevrilmiş nesneyi geçersiniz.  
  
 Bu, belirli adların yinelendiği büyük bir XML ağacı oluşturduğunuzda performansı artırır. Bunu yapmak için, XML <xref:System.Xml.Linq.XName> ağacını oluşturmadan önce nesneleri bildirir ve <xref:System.Xml.Linq.XName> baş harflerine başharfe çevirirsiniz ve ardından öğe ve öznitelik adları için dizeleri belirtmek yerine nesneleri kullanırsınız. Bu teknik, aynı ada sahip çok sayıda öğe (veya öznitelik) oluşturuyorsanız önemli performans kazançları sağlayabilir.  
  
 Kullanıp kullanmadığınıza karar vermek için ön atomizeasyonu senaryonuzla test etmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 Aşağıdaki örnek, XML belgesinin bir ad alanında olduğu aynı tekniği gösterir:  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 Aşağıdaki örnek, gerçek dünyada karşılaşacağınız şeye daha çok benzer. Bu örnekte, öğenin içeriği bir sorgu tarafından sağlanır:  
  
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
  
 Önceki örnek, adların önceden atomlaştırılmayan aşağıdaki örnekten daha iyi performans gösterir:  
  
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

- [Atomize XName ve XNamespace Nesneler (LINQ xml için) (C#)](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
