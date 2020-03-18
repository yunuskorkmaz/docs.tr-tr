---
title: Fonksiyonel Yapı (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635762"
---
# <a name="functional-construction-linq-to-xml-c"></a>Fonksiyonel Yapı (LINQ - XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]*fonksiyonel yapı*adı verilen XML öğeleri oluşturmak için güçlü bir yol sağlar. Fonksiyonel yapı, tek bir ifadede bir XML ağacı oluşturma yeteneğidir.  
  
 Programlama arabiriminin [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel yapıyı etkinleştiren birkaç temel özelliği vardır:  
  
- Oluşturucu <xref:System.Xml.Linq.XElement> içerik için çeşitli bağımsız değişkenler alır. Örneğin, bir alt <xref:System.Xml.Linq.XElement> öğe olur başka bir nesne, geçirebilirsiniz. Öğenin bir <xref:System.Xml.Linq.XAttribute> özniteliği haline gelen bir nesneyi geçirebilirsiniz. Veya bir dize dönüştürülür ve öğenin metin içeriği olur nesne, başka bir tür geçirebilirsiniz.  
  
- Oluşturucu, <xref:System.Xml.Linq.XElement> istediğiniz `params` sayıda <xref:System.Object>nesneyi oluşturucuya geçirebilmeniz için bir dizi tür alır. Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.  
  
- Bir nesne uygularsa, <xref:System.Collections.Generic.IEnumerable%601>nesnedeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir. Koleksiyon <xref:System.Xml.Linq.XElement> içeriyorsa <xref:System.Xml.Linq.XAttribute> veya nesnelere, koleksiyondaki her öğe ayrı olarak eklenir. Bu önemlidir, çünkü bir LINQ sorgusunun sonuçlarını oluşturucuya geçirmenizi sağlar.  
  
 Bu özellikler, bir XML ağacı oluşturmak için kod yazmanızı sağlar. Aşağıda bir örnek verilmiştir:  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Bu özellikler, bir XML ağacı oluşturduğunuzda LINQ sorgularının sonuçlarını kullanan kod yazmanızı da sağlar:  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  