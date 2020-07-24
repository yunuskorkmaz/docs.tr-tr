---
title: İşlevsel oluşturma (LINQ to XML) (C#)
description: LINQ to XML programlama arabiriminin, C# ' de tek bir ifadede bir XML ağacı oluşturma özelliği olan işlevsel oluşturmayı nasıl sağladığını öğrenin.
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: f209a7ef2a4597ec8eeccb3083b77223a27e7a65
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103766"
---
# <a name="functional-construction-linq-to-xml-c"></a>İşlevsel oluşturma (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]*işlevsel oluşturma*adlı XML öğeleri oluşturmak için güçlü bir yol sağlar. İşlevsel oluşturma, tek bir bildirimde bir XML ağacı oluşturma olanağıdır.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Programlama arabiriminin işlevsel oluşturmayı etkinleştiren birkaç temel özelliği vardır:  
  
- <xref:System.Xml.Linq.XElement>Oluşturucu içerik için çeşitli bağımsız değişken türlerini alır. Örneğin, <xref:System.Xml.Linq.XElement> bir alt öğe haline gelen başka bir nesneyi geçirebilirsiniz. <xref:System.Xml.Linq.XAttribute>Öğesinin bir özniteliği haline gelen bir nesneyi geçirebilirsiniz. Ya da bir dizeye dönüştürülen ve öğenin metin içeriği haline gelen başka herhangi bir nesne türünü geçirebilirsiniz.  
  
- <xref:System.Xml.Linq.XElement>Oluşturucuya `params` <xref:System.Object> herhangi bir sayıda nesne geçirebilmeniz için Oluşturucu türünde bir dizi alır. Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.  
  
- Bir nesne uygularsa <xref:System.Collections.Generic.IEnumerable%601> , nesne içindeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir. Koleksiyon <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneler içeriyorsa, koleksiyondaki her öğe ayrı ayrı eklenir. Bir LINQ sorgusunun sonuçlarını oluşturucuya geçirmenize izin sağladığından bu önemlidir.  
  
 Bu özellikler bir XML ağacı oluşturmak için kod yazmanıza olanak sağlar. Aşağıda bir örnek verilmiştir:  
  
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
  
 Bu özellikler ayrıca, bir XML ağacı oluştururken aşağıdaki gibi LINQ sorgularının sonuçlarını kullanan kodu yazmanızı de sağlar:  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  